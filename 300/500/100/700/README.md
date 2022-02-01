# 700 - Render Your Video

Now here comes the magic! Turn your creation into an MP4.

```
$ npm run build
```

The underlying command in package.json is defined as follows:

```
npx remotion render src/index.tsx HelloWorld out/video.mp4
```

Modify it to select a different video to render, or change its output location. Learn about all the options on the [CLI reference page](https://www.remotion.dev/docs/cli).

## 100 - More Ways To Render

### 100 - SSR

Remotion has a full-featured server-side rendering API. Read more about it on the [server-side rendering API](https://www.remotion.dev/docs/ssr).

### 200 - Github Actions

You can also render a [video using a Github Action](https://www.remotion.dev/docs/ssr#render-using-github-actions).

### 300 - Serverless

We are also working on a Serverless solution for rendering videos, [which is in private beta](https://www.remotion.dev/docs/ssr#rendering-a-video-using-serverless)

### 400 - Only Audio

Instead of rendering a video, [you can also just export the audio](https://www.remotion.dev/docs/encoding#audio-only-export).

### 500 - Image Sequence

Instead of encoding as a video, you can use the ```--sequence``` command to output a series of image.

### 600 - Still Images

If you want a single image, you can do so using [the CLI or Node.JS API](https://www.remotion.dev/docs/stills).

## 200 - See Also

- [CLI options](https://www.remotion.dev/docs/cli)
