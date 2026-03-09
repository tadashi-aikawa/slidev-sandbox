---
title: Markdown Documentationのススメ
colorSchema: light
canvasWidth: 1280
themeConfig:
  primary: "#3db680"
background: ./public/attachments/cat-minerva.webp
comark: true
layout: cover
---

# Slidevのレイアウトベーススライド

<span class="text-dimmed">
2026/03/08   Tadashi Aikawa
</span>

---
title: Agenda
layout: chapter-divider
---

---
title: Chapter1
layout: chapter-divider
activeChapter: 1
---

---

# 普通のスライド

ここに説明を書いたり。

- 箇条書きを
- 書いたり

---
layout: fact
---

# fact

名言だったり、参考文献・グラフなどの事実を扱うときに使う。

すべてが中央寄りになる。

```ts
const a = 1;
const b = 2;
// コードブロックには向かない。その場合は `layout: center` を使おう
```

---
layout: center
---

# center

中央にコンテンツを表示したいときに使う。

中央揃えではないので注意。

```ts
const a = 1;
const b = 2;
console.log(a + b);
```

---
layout: image
image: ./public/attachments/cat-minerva.webp
---

### 画像を全面表示したい場合

---

# 動画再生 `自動再生不要ならautoplayは外す`

<SlidevVideo controls autoplay="once" autoreset="slide" class="mx-auto h-90%">
    <source src="./public/attachments/colot.mp4" type="video/mp4" />
</SlidevVideo>

---
layout: image-left
image: https://publish-01.obsidian.md/access/35d05cd1bf5cc500e11cc8ba57daaf88/Notes/attachments/colot.webp
background-size: contain
---

# 左半分を画像にしたい場合

```yaml
background-size: contain
```

を追加することで縦が収まるサイズに調整している。

---
layout: image-right
image: https://publish-01.obsidian.md/access/35d05cd1bf5cc500e11cc8ba57daaf88/Notes/attachments/obsidian-mini2.webp
background-size: contain
---

# 右半分を画像にしたい場合

```yaml
background-size: contain
```

を追加することで縦が収まるサイズに調整している。

---
layout: iframe
url: https://minerva.mamansoft.net/Notes/%E3%83%9F%E3%83%8D%E3%83%AB%E3%83%B4%E3%82%A1
---

# 全面iframe

---

## Richリンクカード

<div class="link-card-v2">
  <div class="link-card-v2-site">
    <img class="link-card-v2-site-icon" src="https://github.githubassets.com/favicons/favicon.svg" />
    <span class="link-card-v2-site-name">GitHub</span>
  </div>
  <div class="link-card-v2-title">
    GitHub - tadashi-aikawa/slidev-preview.nvim: Neovim plugin that syncs your Slidev presentation in the browser with your cursor position in `slides.md`.
  </div>
    <div class="link-card-v2-content">
    Neovim plugin that syncs your Slidev presentation in the browser with your cursor position in `slides.md`. - tad ... 
  </div>
  <img class="link-card-v2-image" src="https://opengraph.githubassets.com/535fcff3e8d6f996c4e900572f4b30b10d7ddffd65056996751e1b63ac0cffd4/tadashi-aikawa/slidev-preview.nvim" />
  <a href="https://github.com/tadashi-aikawa/slidev-preview.nvim"></a>
</div>

---
layout: two-cols-header
---

# ヘッダの下を左右に分割

::left::

- 左側

::right::

- 右側

---
layout: two-cols
---

# ヘッダ含めて左右に分割(左側のタイトル)

- 左側

::right::

# ヘッダ含めて左右に分割(右側のタイトル)

- 右側

---
title: Chapter2
layout: chapter-divider
activeChapter: 2
---

---
layout: fact
---

# コードブロックの表現は多い

---

# 普通のコードブロック

```lua
return {
  -- 'tadashi-aikawa/slidev-preview.nvim',
  dir = "~/git/github.com/tadashi-aikawa/slidev-preview.nvim",
  cmd = "SlidevPreviewStart",
  opts = {},
}
```

---

# ファイル名・行番号つき

```lua [slidev-preview.lua ~i-vscode-icons:file-type-lua~] {*}{lines: true}
return {
  -- 'tadashi-aikawa/slidev-preview.nvim',
  dir = "~/git/github.com/tadashi-aikawa/slidev-preview.nvim",
  cmd = "SlidevPreviewStart",
  opts = {},
}
```

※ ヘッドマターで `lineNumbers: true` を設定すれば `lines: true` は不要

---

# コードグループ

::code-group

```sh [npm]
npm i @slidev/cli
```

```sh [yarn]
yarn add @slidev/cli
```

```sh [pnpm]
pnpm add @slidev/cli
```

::

---

# 高度なコードブロック

`{*}{maxHeight:}` で指定する。`%` が良さげ。

```vue [MethodBadge.vue] {*}{maxHeight:'80%', lines: true}
<script setup lang="ts">
import type { PrimitiveProps } from "reka-ui";
import type { HTMLAttributes } from "vue";
import type { BadgeVariants } from ".";
import { reactiveOmit } from "@vueuse/core";
import { Primitive } from "reka-ui";
import { cn } from "@/lib/utils";
import { badgeVariants } from ".";

const props = defineProps<
  PrimitiveProps & {
    variant?: BadgeVariants["variant"];
    class?: HTMLAttributes["class"];
  }
>();

const delegatedProps = reactiveOmit(props, "class");
</script>

<template>
  <Primitive
    data-slot="badge"
    :class="cn(badgeVariants({ variant }), props.class)"
    v-bind="delegatedProps"
  >
    <slot />
  </Primitive>
</template>
```

---

# 高度なコードブロック

ハイライト指定は `{1,10}` や `{5-7}` のように。`|` 区切りでアニメーション。

```vue [MethodBadge.vue] {1,18|2-8|10-15|17}{maxHeight:'80%', lines: true}
<script setup lang="ts">
import type { PrimitiveProps } from "reka-ui";
import type { HTMLAttributes } from "vue";
import type { BadgeVariants } from ".";
import { reactiveOmit } from "@vueuse/core";
import { Primitive } from "reka-ui";
import { cn } from "@/lib/utils";
import { badgeVariants } from ".";

const props = defineProps<
  PrimitiveProps & {
    variant?: BadgeVariants["variant"];
    class?: HTMLAttributes["class"];
  }
>();

const delegatedProps = reactiveOmit(props, "class");
</script>

<template>
  <Primitive
    data-slot="badge"
    :class="cn(badgeVariants({ variant }), props.class)"
    v-bind="delegatedProps"
  >
    <slot />
  </Primitive>
</template>
```

---

# 高度なコードブロック

アニメーション表示 `md magic-move`

````md magic-move {lines: true}
```ts
const x = 1;
```

```ts
const x = 1;
const y = 1;
```

```ts
const x = -1;
```
````

---
layout: fact
---

TODO: 続き
