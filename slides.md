---
theme: default
class: 'text-center'
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
fonts:
  sans: 'Noto Sans JP'
  serif: 'Noto Serif JP'
---

# Slidevを<span class="blue">'Hack'</span>し<br><span class="vivit">'豊かなSlide'</span>を作る

<p class="name">hiroko_ino</p>

<Decoration />

<style>
.blue {
  color: var(--main-color-blue);
  font-style: italic;
  margin: 0 15px 0 5px;
}

.vivit {
  color: var(--main-color-vivit);
  margin-right: 10px;
}

.name {
  font-size: 30px;
  margin-top: 40px;
  color: var(--main-color-black);
  opacity: 1;
}
</style>

---
layout: image-right
image: ./uribou_profile.jpg
---

# 自己紹介

- hiroko_ino
- Web フロントエンドエンジニア
- 普段はReact・Web制作の人
- 湘南住み
- 🐗 名字がイノシシ

<style>
.slidev-layout ul {
  margin-top: 40px;
}

.slidev-layout li {
  font-size: 24px;
}

.slidev-layout li + li {
  margin-top: 8px;
}
</style>

---

# Slidevとは?

https://sli.dev/

Slidevは開発者向けに設計されたスライドツールです。 以下の機能で構成されています。

- 📝 **Text-based** - マークダウンを使用し、スタイルを設定出来ます
- 🎨 **Themable** - npm packageを使用しテーマをシェア出来ます
- 🧑‍💻 **Developer Friendly** - コードハイライト, オートコンプリートを使用したライブコーディング
- 🤹 **Interactive** - Vueコンポーネントの埋め込みで表現を強化します
- 🎥 **Recording** - ビルトインの録画とカメラビューがあります
- 📤 **Portable** - PDFへのエクスポート, PNG, ホスティング可能なSPA
- 🛠 **Hackable** - Webページで可能なことは何でも


<style>
.slidev-layout li {
  list-style: none;
  padding-left: 0;
  margin-left: 0;
}

.slidev-layout li + li {
  margin-top: 8px;
}

.slidev-layout li::before {
  content: "✅";
  margin-right: 13px;
}
</style>

---

# おすすめポイント

- マークダウン内にhtmlを書いていけばかなりの自由度
- Windi CSSを用いたスタイリング https://windicss.org/
- ページごとに設定出来るScopedなstyle
- 簡単にホスティング（Netlify, vercel, GitHub Pages）
- 『Webページで可能なことは何でも』の言葉とおり、VueやCSSの知識で好きなようにHack出来る（このスライドのように！）

CSSの知識がある人は心地よくレイアウト出来るのに感動すると思う！

<style>
.slidev-layout ul {
  margin-top: 40px;
}

.slidev-layout li + li {
  margin-top: 8px;
}
</style>

---
layout: cover
class: 'text-center'
---
# 基本的な使い方

<Decoration />

<style>
h1 {
  color: var(--main-color-blue);
}
</style>
---

# 【基本】始め方

```
With NPM:
$ npm init slidev
With Yarn:
$ yarn create slidev
```

<div class="after" v-click>
↓のようなプロジェクトフォルダが作成される

```
components/ => このフォルダ内のVueファイルがコンポーネントとして扱える
.gitignore
.npmrc
.netlify.toml => Netlifyホスティング用
package.json
README.md
slides.md => このファイルが単一のエントリーポイントとなり、プロジェクト内で一つのスライドを生成する
vercel.json => Vercelホスティング用
yarn.lock
```
</div>

<style>
  .after {
    margin-top: 30px;
  }
</style>

---

# 【基本】マークダウンの記法

<img src="/markdown.png" width="600" class="shadow" />

---
layout: cover
class: 'text-center'
---
# カスタマイズ

<Decoration />

<style>
h1 {
  color: var(--main-color-blue);
}
</style>

---

# 変数を扱う

$slidev.nav.currentPage（現在のページ番号）など、グローバルに用意されている変数はいくつかある
https://sli.dev/custom/vue-context.html

独自の変数を使う方法は、ドキュメント内を"variable"で検索したけどなさそう？

CSSに変数を使いたいなら./style.cssもしくは./styles/xx.css（グローバルのCSSファイル）を作成し、CSS カスタムプロパティでよさそう

```css
// style.css
:root {
  --main-color: #FB98B7;
  --main-color-sheer: #FFC0D1;
  --main-color-vivit: #FF48A5;
  --main-color-red: #FF005F;
  --main-color-blue: #4DCCD2;
  --main-color-black: #333;
}
```

---

# カメラにborderをつける

```html
<!--v-if-->
<div id="slidev-goto-dialog" class="fixed right-5 bg-main transform transition-all -top-20" shadow="~" p="x-4 y-2" border="~ transparent rounded dark:gray-400 dark:opacity-25" data-v-7df26b02="">
  <input type="number" disabled="" class="outline-none bg-transparent" placeholder="Goto..." data-v-7df26b02="">
</div>
<div class="fixed z-10" style="left: 838.861px; top: 432.301px;">
  <div class="rounded-full shadow bg-gray-400 bg-opacity-10 overflow-hidden object-cover" style="width: 177px; height: 177px;">
    <video autoplay="" class="object-cover min-w-full min-h-full rounded-full" style="transform: rotateY(180deg);"></video>
  </div>
  <div class="absolute bottom-0 right-0 rounded-full bg-main shadow opacity-0 shadow z-30 hover:opacity-100 dark:border dark:border-true-gray-700" style="width: 14px; height: 14px; top: 144.087px; left: 144.087px; cursor: nwse-resize;">
  </div>
</div>
<!--v-if-->
```

Windi CSSのクラスだけが並んでいる…🤔

<div v-click>
↓↓で解決

```css
// style.css等
#slidev-goto-dialog + div > div {
  なにかする
}
```
</div>

---

# 独自のプログレスバーを作る

このページの下についているページの現在地を表すバーです😁

```vue
// global-bottom.vue
<template>
  <Progress
    v-if="$slidev.nav.currentPage !== 1 && $slidev.nav.currentLayout!== 'end'"
    :current="$slidev.nav.currentPage"
    :total="$slidev.nav.total" />
</template>
```

---

```vue
// components/Progres.vue
<template>
    <div class="absolute z-50 bottom-5 left-0 right-0 flex justify-center">
        <div class="w-50 relative h-1 bg-green-500/50 rounded-full overflow-hidden">
            <span class="absolute h-full bg-gray-500 transition-all duration-300" :style="style"></span>
        </div>
    </div>
</template>

<script lang="ts">
  export default {
    name: "Progress",
    // propsを受け取る
    computed: {
      style() {
        return {
          width: `${100 / (this.total - 1)}%`,
          left: `${100 / (this.total - 1) * (this.current - 2)}%`,
        }
      }
    }
  };
```


