# 600 - Preview Your Video

You can start the preview server of Remotion using

```
$ npm start
```

If you are using a custom template, use

```
$ npx remotion preview src/index.tsx
```

where ```src/index.tsx``` is the file where ```registerRoot()``` is called.

![timeline](https://user-images.githubusercontent.com/12828104/151999247-223cfb33-21fc-4675-87bf-ecebd1eaaf66.png)

## 100 - Preview Controls

Use the ```>``` button or ```Space``` to play your video.

Use the ```|<``` and ```>|``` buttons to jump 1 frame backwards or forwards. You can also use the left arrow or right arrow to do so. If you hold the ```Shift``` key, you jump 1 second at a time.

## 200 - Toggling Transparency Mode

By default, the background of your video is a checkerboard pattern signifying that the pixels are transparent. You can press ```checkerboard``` button to disable this behavior which will render a black background.

## 300 - In / Out Markers

Use the ```[``` and ```]``` buttons to set an In or Out marker. When you play the video again, only the range within the markers will play.

You may also set markers using the ```I``` and ```O``` keys.

To clear a marker, make sure your playback head is at the point of a marker and press the button you pressed to activate it again. Or use the ```X``` key to clear both markers.

