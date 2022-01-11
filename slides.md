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

# Slidevとは?

https://sli.dev/

Slidevは開発者向けに設計されたスライドツールです。 以下の機能で構成されています。

- 📝 **Text-based** - マークダウンを使用し、スタイルを設定出来ます
- 🎨 **Themable** - npm packageを使用しテーマをシェア出来ます
- 🧑‍💻 **Developer Friendly** - コードハイライト, オートコンプリートを使用したライブコーディング
- 🤹 **Interactive** - Vueコンポーネントの埋め込みで表現を強化します
- 🎥 **Recording** - ビルトインの録画とカメラビューがあります
- 📤 **Portable** - PDFへのエクスポート, PNG, ホスティング可能なSPA
- 🛠 **Hackable** - Webページで可能なことは何でも！


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

ドキュメント内を"variable"で検索したけどなさそう？

CSSに変数を使いたいなら./style.css（グローバルのCSSファイル）を作成し、CSS カスタムプロパティでよさそう

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
// style.css
#slidev-goto-dialog + div > div {
  border: 3px solid var(--main-color-sheer);
}
```
</div>
