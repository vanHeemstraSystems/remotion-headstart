# 500 - Reuse Components Using Sequences

Let's say we want to show two titles that both fade in after each other.

In order to make a title reusable, we first factor it out into it's own component.

```
import {interpolate, useCurrentFrame} from 'remotion'

const Title: React.FC<{title: string}> = ({title}) => {
    const frame = useCurrentFrame()
    const opacity = interpolate(frame, [0, 20], [0, 1], {extrapolateRight: 'clamp'})

    return (
      <div style={{opacity}}>{title}</div>
    )
}

export const MyVideo = () => {
  return (
    <div style={{ flex: 1, justifyContent: "center", alignItems: "center" }}>
      <Title title="Hello World" />
    </div>
  );
};
```

Now we can use the ```<Sequence>``` component to limit the duration of the first title and time-shift the appearance of the second title.

```
import { Sequence } from "remotion";

export const MyVideo = () => {
  return (
    <div
      style={{
        flex: 1,
        justifyContent: "center",
        alignItems: "center",
        backgroundColor: "white",
      }}
    >
      <Sequence from={0} durationInFrames={40}>
        <Title title="Hello" />
      </Sequence>
      <Sequence from={40}>
        <Title title="World" />
      </Sequence>
    </div>
  );
};
```

You should see two titles appearing after each other. Titles which are not shown during a frame are unmounted. This is why the layout did not shift (as it does in HTML) when you added a second title. If you want the titles to overlap in time, use absolute positioning if necessary.

**Tip**: Create a ```Component``` in Strapi (Headless CMS, see strapi.io) for "Sequence", thus containing the following properties:

- name: Text (Optional)
- component: Relation to another Strapi ContentType: Composition (Optional)
- from: Number (Numeric, no Decimals, Mandatory)
- durationInFrames: Text (Optional)
- layout: Text (Optional)

In a previous tip we also recommended to create a ```Component``` in Strapi for "Composition". The "Sequence" can thus contain none, one or more "Compositions".
