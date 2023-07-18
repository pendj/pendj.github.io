---
title: "Stack使用方式"
date: 2023-07-18T12:11:12+08:00
---

### Shortcodes
Stack 附带了一组可以在内容中使用的短代码。
此页面仅包含特定于 Stack 的短代码。Hugo 的内置短代码记录在此处。
> 下面为了避免代码执行,在<>侧加了转义符'\',使用时去掉

#### 哔哩哔哩视频
```markdown
{{\< bilibili VIDEO_ID PART_NUMBER \>}}
```

#### 腾讯视频
```markdown
{{\< tencent VIDEO_ID \>}}
```

#### Youtube 视频
```markdown
{{\< youtube VIDEO_ID \>}}
```

#### 通用视频文件
```markdown
{{\< video VIDEO_URL \>}}
{{\< video src="VIDEO_URL" autoplay="true" poster="./video-poster.png" \>}}
```
可以VIDEO_URL是 URL 或相对于目录的路径static。
例如，src="/video/my-video.mp4"将嵌入您网站文件夹的视频文件static/video/my-video.mp4。
该autoplay属性是可选的。它可用于指定是否应自动播放视频。该poster属性是可选的。它可用于指定视频的海报图像。

#### GitLab
```markdown
{{\< gitlab SNIPPET_ID \>}}
```
可以SNIPPET_ID在片段的 URL 中找到。例如，https://gitlab.com/-/snippets/1234567 为1234567。

#### 引用
```markdown
{{\< quote author="A famous person" source="The book they wrote" url="https://en.wikipedia.org/wiki/Book">}}
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
{{< /quote \>}}
```