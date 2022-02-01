# 400 - Animation Properties

***Animation is all about how properties change over time***. 

Let's start with a simple example, let's say we want to create a fade in animation.

If we want to fade the text in over 20 frames, we need to gradually change the ```opacity``` style over time so that it goes from 0 to 1.

```
export const MyVideo = () => {
  const frame = useCurrentFrame();

  const opacity = frame >= 20 ? 1 : frame / 20;

  return (
    <div
      style={{
        flex: 1,
        justifyContent: "center",
        alignItems: "center",
        opacity: opacity,
      }}
    >
      Hello World!
    </div>
  );
};
```

## 100 - Using the Interpolate Helper Function

Using the ```interpolate``` function can make animations more readable. The function takes 4 arguments:

1. The input value
2. The range values which the input can assume
3. The range of values that you want to map the input to
4. Optional settings

```
import { interpolate, useCurrentFrame } from "remotion";

export const MyVideo = () => {
  const frame = useCurrentFrame();

  const opacity = interpolate(frame, [0, 20], [0, 1], {
    extrapolateRight: "clamp",
  });

  return (
    <div
      style={{
        flex: 1,
        justifyContent: "center",
        alignItems: "center",
        opacity: opacity,
      }}
    >
      Hello World!
    </div>
  );
};
```

In this example, we map the frames 0 to 20 to their opacity values ```(0, 0.05, 0.1, 0.15 ...)``` and use the ```extrapolateRight``` setting to clamp the output so that it never becomes bigger than 1.

## 200 - Using Spring Animations

Spring animations are beautiful way to put things into motion and make them natural. Remotion includes a helper function to make spring animations easy! This time, let's animate the scale of the text.

```
import { spring, useCurrentFrame, useVideoConfig } from "remotion";

export const MyVideo = () => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();

  const scale = spring({
    fps,
    from: 0,
    to: 1,
    frame,
  });

  return (
    <div
      style={{
        flex: 1,
        justifyContent: "center",
        alignItems: "center",
      }}
    >
      <div style={{ transform: `scale(${scale})` }}>Hello World!</div>
    </div>
  );
};
```

You should see the text 'jump in'. The default spring configuration leads to a little bit of overshoot, meaning the text will bounce a little bit. See the reference page about the ```spring``` function to learn how to customize your spring animations.

## 300 - Always Animate Using useCurrentFrame()

Watch out for flickering issues during rendering that arise if you write animations that are not driven by [useCurrentFrame()](https://www.remotion.dev/docs/use-current-frame) - for example CSS transitions.

[Read more about how Remotion's rendering works](https://www.remotion.dev/docs/flickering) - understanding it will help you avoid issues down the road.
