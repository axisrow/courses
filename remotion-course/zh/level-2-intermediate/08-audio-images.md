---
title: "添加音频和图片"
weight: 8
bookToc: true
---

# 添加音频和图片

视频不只是文字。让我们为 Remotion 项目添加音频和图片。

## 添加图片

将图片放在项目的 `public` 文件夹中，然后使用：

```tsx
import { Img, staticFile } from "remotion";

export const MyScene = () => {
  return <Img src={staticFile("photo.jpg")} />;
};
```

`staticFile()` 指向 `public` 文件夹中的文件。使用 `<Img>` 组件（不是 HTML `<img>`）——它会等图片加载完成后再渲染。

## 添加音频

```tsx
import { Audio, staticFile } from "remotion";

export const MyScene = () => {
  return (
    <>
      <Audio src={staticFile("music.mp3")} />
      <div>视觉内容</div>
    </>
  );
};
```

## 控制音量

```tsx
<Audio
  src={staticFile("music.mp3")}
  volume={(f) =>
    interpolate(f, [0, 30], [0, 1], {
      extrapolateRight: "clamp",
    })
  }
/>
```

音频在30帧内淡入。

## 序列中的音频

`<Sequence>` 中的音频只在该序列期间播放：

```tsx
<Sequence from={60} durationInFrames={120}>
  <Audio src={staticFile("narration.mp3")} />
</Sequence>
```

## 使用远程 URL

也可以使用网址：

```tsx
<Img src="https://example.com/photo.jpg" />
<Audio src="https://example.com/music.mp3" />
```

## 总结

使用 `<Img>` 添加图片，`<Audio>` 添加声音。两者都支持本地文件（通过 `staticFile()`）和远程 URL。
