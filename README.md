<div align="center">

# 🎨 CSS Fundamentals: Hands-On Experiments

**Small, focused demos to understand how CSS really works**

</div>

---

## 📖 About This Repository

This repository is a collection of mini-projects I built while learning CSS. Each folder contains a single `index.html` file that isolates **one concept**, so the effect of every property is easy to see and experiment with.

No frameworks, no build tools. Just HTML and CSS.

---

## 📑 Table of Contents

1. [Project Structure](#-project-structure)
2. [Experiment 1: The `display` Property](#-experiment-1-the-display-property)
3. [Experiment 2: Viewport Units & Box Sizing](#-experiment-2-viewport-units--box-sizing)
4. [Experiment 3: CSS Specificity](#-experiment-3-css-specificity)
5. [How to Run](#-how-to-run)
6. [Key Takeaways](#-key-takeaways)
7. [Roadmap](#-roadmap)

---

## 📂 Project Structure

```
css-fundamentals/
│
├── 01-display-property/
│   └── index.html
│
├── 02-viewport-units/
│   └── index.html
│
├── 03-css-specificity/
│   └── index.html
│
└── README.md
```

> 💡 Rename the folders to match your own layout. Each `index.html` is fully standalone.

---

## 🧱 Experiment 1: The `display` Property

📁 `01-display-property/index.html`

### 🎯 Goal
Understand how the `display` property changes the way elements flow on the page, and how `display: none` differs from `visibility: hidden`.

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Concept</th>
    <th>What it does</th>
  </tr>
  <tr>
    <td><code>display: inline-block</code></td>
    <td>Element sits in line with other content like text, but still accepts <code>width</code>, <code>height</code>, <code>padding</code> and <code>margin</code>.</td>
  </tr>
  <tr>
    <td><code>display: none</code></td>
    <td>Element is <b>removed from the layout entirely</b>. It takes up no space.</td>
  </tr>
  <tr>
    <td><code>visibility: hidden</code></td>
    <td>Element becomes <b>invisible but still occupies its space</b> in the layout.</td>
  </tr>
  <tr>
    <td><code>* { margin: 0; padding: 0; }</code></td>
    <td>A simple CSS reset that removes the browser's default spacing.</td>
  </tr>
</table>

### 🧪 Code Highlight

```css
.box {
  border: 2px solid blue;
  display: inline-block;
  width: 344px;
  padding: 45px;
  margin: 34px;
}

.box1 {
  /* display: none; */
  /* visibility: hidden; */
}
```

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Open the file as-is. Both boxes appear side by side (if your window is wide enough) because they are `inline-block`.
2. Uncomment `display: none;` in `.box1`. The first box vanishes and the second box **shifts into its place**.
3. Comment that out and uncomment `visibility: hidden;` instead. The first box becomes invisible, but **the empty space stays**.
4. Notice the two `<span>` elements at the bottom. They are `inline` by default, so they sit on the same line and ignore width and height.

</details>

---

## 📐 Experiment 2: Viewport Units & Box Sizing

📁 `02-viewport-units/index.html`

### 🎯 Goal
Build layouts that adapt to the screen size using **viewport units** instead of fixed pixels, and see how `box-sizing`, `min-height` and `em` behave in nested elements.

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Concept</th>
    <th>Why it matters</th>
  </tr>
  <tr>
    <td><code>vw</code> / <code>vh</code></td>
    <td>1<code>vw</code> = 1% of viewport width, 1<code>vh</code> = 1% of viewport height. Lets elements scale with the browser window.</td>
  </tr>
  <tr>
    <td><code>box-sizing: border-box</code></td>
    <td>Includes padding and border inside the declared width and height, making sizing predictable.</td>
  </tr>
  <tr>
    <td><code>margin: 0 auto</code></td>
    <td>Horizontally centers a block element that has a defined width.</td>
  </tr>
  <tr>
    <td><code>min-height</code> vs <code>height</code></td>
    <td><code>min-height</code> lets the container <b>grow with its content</b> instead of overflowing.</td>
  </tr>
  <tr>
    <td><code>em</code> units</td>
    <td>Relative to the <b>parent's font size</b>. Here <code>2em</code> on an <code>18px</code> parent gives <code>36px</code>.</td>
  </tr>
  <tr>
    <td>Percentage widths</td>
    <td>Child <code>width: 50%</code> is relative to its parent, so nested elements shrink step by step (50% of 50%).</td>
  </tr>
  <tr>
    <td>Child combinator <code>&gt;</code></td>
    <td><code>.container &gt; div</code> targets only <b>direct</b> children, not every descendant.</td>
  </tr>
</table>

### 🧪 Code Highlight

```css
.box {
  box-sizing: border-box;
  width: 80vw;
  height: 10vh;
  margin: 0 auto;
  border: 2px solid black;
  background-color: aquamarine;
}

.container {
  box-sizing: border-box;
  width: 80vw;
  min-height: 80vh;      /* grows if content needs more room */
  margin: 23px auto;
  font-size: 18px;
}

.container > div {
  font-size: 2em;        /* 2 × 18px = 36px */
  width: 50%;
}

.container > div > div {
  width: 50%;            /* 50% of the parent, which is itself 50% */
}
```

### 🧠 Visual Breakdown

<table>
  <tr>
    <td align="center"><b>Element</b></td>
    <td align="center"><b>Border color</b></td>
    <td align="center"><b>Width</b></td>
  </tr>
  <tr>
    <td><code>.container</code></td>
    <td>⬛ Black</td>
    <td>80% of viewport</td>
  </tr>
  <tr>
    <td><code>.container &gt; div</code></td>
    <td>🟥 Red</td>
    <td>50% of container</td>
  </tr>
  <tr>
    <td><code>.container &gt; div &gt; div</code></td>
    <td>🟦 Blue</td>
    <td>50% of the red box</td>
  </tr>
</table>

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Resize your browser window and watch the boxes scale smoothly.
2. Swap `min-height: 80vh` for `height: 80vh` and add more text. The content overflows instead of the container growing.
3. Remove `box-sizing: border-box` and observe the elements become slightly larger than expected because of the border.
4. Change `font-size` on `.container` and see the nested text resize with it, thanks to `em`.

</details>

---

## ⚖️ Experiment 3: CSS Specificity

📁 `03-css-specificity/index.html`

### 🎯 Goal
Understand **which CSS rule wins** when several rules target the same element and set the same property.

### 🧪 The Setup

One `<h1>` element, four competing color rules:

```html
<h1 class="yellow cred cpurple" data-x="a">CSS Specificity</h1>
```

```css
h1            { color: aqua; }     /* specificity: 1  */
.cpurple      { color: purple; }   /* specificity: 10 */
[data-x="a"]  { color: maroon; }   /* specificity: 10 */
h1.yellow     { color: yellow; }   /* specificity: 11 */
.cred         { color: red; }      /* specificity: 10 */
```

### 📊 Specificity Scoreboard

<table>
  <tr>
    <th>Selector</th>
    <th>Type</th>
    <th>Score</th>
    <th>Result</th>
  </tr>
  <tr>
    <td><code>h1</code></td>
    <td>Element</td>
    <td align="center">1</td>
    <td>❌ Loses</td>
  </tr>
  <tr>
    <td><code>.cpurple</code></td>
    <td>Class</td>
    <td align="center">10</td>
    <td>❌ Loses</td>
  </tr>
  <tr>
    <td><code>[data-x="a"]</code></td>
    <td>Attribute</td>
    <td align="center">10</td>
    <td>❌ Loses</td>
  </tr>
  <tr>
    <td><code>.cred</code></td>
    <td>Class</td>
    <td align="center">10</td>
    <td>❌ Loses</td>
  </tr>
  <tr>
    <td><code>h1.yellow</code></td>
    <td>Element + Class</td>
    <td align="center"><b>11</b></td>
    <td>🏆 <b>Wins → heading is yellow</b></td>
  </tr>
</table>

### 📚 Specificity Cheat Sheet

| Selector type | Example | Weight |
|---|---|---|
| Inline styles | `style="..."` | 1000 |
| ID | `#header` | 100 |
| Class, attribute, pseudo-class | `.card`, `[type="text"]`, `:hover` | 10 |
| Element, pseudo-element | `h1`, `::before` | 1 |

> ℹ️ The scores above are a simplified teaching model. Real browsers compare specificity as separate tiers (IDs, then classes, then elements) rather than one summed number, but the simplified version works well for learning.

### 💡 The Lesson

When specificity is **equal**, the rule that appears **last** in the stylesheet wins. When specificity **differs**, the more specific selector wins **regardless of order**. Notice that `h1.yellow` is defined before `.cred`, yet it still wins.

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Delete the `h1.yellow` rule. Now three rules tie at 10, so the last one (`.cred`) wins and the heading turns **red**.
2. Move `.cpurple` to the bottom of the stylesheet. It now wins the tie and the heading turns **purple**.
3. Add `#title` as an id on the `<h1>` and style it. An ID beats all of them.

</details>

---

## 🚀 How to Run

No installation needed.

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git

# 2. Move into the project
cd <your-repo-name>

# 3. Open any experiment in your browser
open 01-display-property/index.html      # macOS
start 01-display-property/index.html     # Windows
xdg-open 01-display-property/index.html  # Linux
```

💡 **Tip:** Use the VS Code **Live Server** extension to see changes instantly as you edit.

---

## 🎓 Key Takeaways

<table>
  <tr>
    <td>✅</td>
    <td><code>display: none</code> removes an element from the layout; <code>visibility: hidden</code> only hides it.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Viewport units (<code>vw</code>, <code>vh</code>) make layouts responsive without media queries.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>box-sizing: border-box</code> makes sizing far more predictable.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>min-height</code> is usually safer than a fixed <code>height</code> for content containers.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Specificity beats source order. Order only matters when specificity is tied.</td>
  </tr>
</table>

---

## 🗺️ Roadmap

- [x] `display` property
- [x] Viewport units and box model
- [x] CSS specificity
- [ ] Flexbox
- [ ] CSS Grid
- [ ] Positioning (`relative`, `absolute`, `fixed`, `sticky`)
- [ ] Media queries and responsive design
- [ ] Transitions and animations

---

<div align="center">

### ⭐ If you found this helpful, consider giving the repo a star!

Made with ❤️ while learning CSS

</div>
