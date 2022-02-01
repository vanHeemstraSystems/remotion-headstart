# 300 - The Fundamentals

The basic idea behind Remotion is that we'll give you a frame number and a blank canvas, and the freedom to render anything you want using [React.js](https://reactjs.org/).

```
import { useCurrentFrame } from "remotion";
 
export const MyVideo = () => {
  const frame = useCurrentFrame();
 
  return (
    <div style={{ flex: 1, justifyContent: "center", alignItems: "center" }}>
      The current frame is {frame}.
    </div>
  );
};
```

A video is a function of images over time. If you change content every frame, you'll end up with an animation.

## 100 - Video Properties

A video has 4 properties:

- **width** and **height** in pixels.
- **durationInFrames**: The number of frames which the video is long.
- **fps**: The amount of frames per second. 

The duration in frames divided by FPS results in the duration in seconds.

These properties are variable and you can reuse a component multiple times with different properties. This is why you better not hard-code these properties, but instead derive them from the [useVideoConfig()](https://www.remotion.dev/docs/use-video-config) hook:

```
import { useVideoConfig } from "remotion";
 
export const MyVideo = () => {
  const { fps, durationInFrames, width, height } = useVideoConfig();
 
  return (
    <div style={{ flex: 1, justifyContent: "center", alignItems: "center" }}>
      This video is {durationInFrames / fps} seconds long.
    </div>
  );
};
```

A video's first frame is **0** and it's last frame is **durationInFrames - 1**.

## 200 - Defining Compositions

Compositions are components with the above mentioned metadata. You can define compositions in ```src/Video.tsx``` to make them show up in the left sidebar.

```
export const RemotionVideo: React.FC = () => {
  return (
    <>
      <Composition
        id="MyVideo"
        component={MyVideo}
        durationInFrames={150}
        fps={30}
        width={1920}
        height={1080}
      />
    </>
  );
};
```

**Tip**: Create a ```Component``` in Strapi (Headless CMS, see strapi.io) for "Composition", thus containing the following properties:

- id: Text (Unique, Mandatory)
- component: Relation to another Strapi ContentType: Component
- durationInFrames: Number (Numeric, no Decimals)
- fps: Number (Numeric, Decimals allowed)
- width: Number (Numeric, no Decimals)
- height: Number (Numeric, no Decimals)

So in addition, also create a ```Component``` in Strapi for "Component".

With Strapi, you can decouple your frontend (here: Remotion) from your backend (here: Strapi) and store all your Compositions and Components in Strapi. Strapi can store these in a database or file.

Remember that if you like, you can register multiple compositions that rely on the same component. For example, if you like to make a square video for social media feeds, and a portrait video for Stories, you can reuse the component and try to make it 'responsive'.

Besides the ```<Composition />``` component, you can also use a ```<Still />``` component and define a still image rather than a video.

**Tip**: Create a ```Component``` in Strapi (Headless CMS, see strapi.io) for "Still", thus containing the following properties:

- id: Text (Unique, Mandatory)
- component: Relation to another Strapi ContentType: Component
- width: Number (Numeric, no Decimals)
- height: Number (Numeric, no Decimals)
