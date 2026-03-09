# Code Showcase — Interactive Language Demo

An interactive, browser-based code showcase built as a single HTML file. Demonstrates advanced programming across 
JavaScript, Python, and C++ through real-world problems in audio DSP, physics simulation, and systems programming.

----------------------------------------------------------------------------------------------------------------
## What It Does

Three tabbed panels each present a realistic, non-trivial code sample with syntax highlighting and a simulated console output. 

Click **▶ RUN** on any panel to animate the output.

What it demonstrates: 
JavaScript: "audioReactiveEngine.js"- Web Audio API, async generators, private class fields, FFT band analysis
Python: "particle_field.py"- NumPy vectorized physics, dataclasses, Einstein summation, generator streaming
C++: "SignalProcessor.cpp" Template metaprogramming, biquad DSP, lock-free ring buffer, C++23 features

----------------------------------------------------------------------------------------------------------------

## Usage

No build step. No dependencies. No npm install.

```bash
# Option 1 — open directly
open code-showcase.html

# Option 2 — serve locally
python -m http.server 8000
# then visit http://localhost:8000/code-showcase.html
```

To deploy on GitHub Pages, push to a repo and enable Pages from the repository settings. The file will be live at:

```
https://<your-username>.github.io/<repo-name>/code-showcase.html
```

-------------------------------------------------------------------------------------------------------------------

## File Structure

```
code-showcase.html    # everything — HTML, CSS, JS in one file
README.md
```

The file is fully self-contained. Fonts load from Google Fonts (requires internet); everything else is inline.

-------------------------------------------------------------------------------------------------------------------

## Customization

All code samples and console outputs are defined as plain arrays near the bottom of the `<script>` block — no framework, no bundler.

**To swap in your own code samples**, find the `codes` object and replace the HTML string arrays:

```js
const codes = {
  js:  [ /* one string per line */ ],
  py:  [ /* one string per line */ ],
  cpp: [ /* one string per line */ ]
};
```

Each line is an HTML string. Use the built-in span classes for syntax coloring:

| Class | Color | Use for |
| `.kw` | purple | keywords (`class`, `const`, `if`) |
| `.fn` | blue | function names |
| `.str` | green | strings |
| `.num` | orange | numbers |
| `.cm` | gray italic | comments |
| `.tp` | yellow | types / class names |
| `.op` | cyan | operators |

**To swap console output**, edit the `outputs` object directly below `codes`. Each entry takes a `text` string and an optional `cls` for coloring:

```js
{ text: 'some output line', cls: 'accent-js' }   // yellow
{ text: 'a result value',   cls: 'result' }       // white bold
{ text: 'a dim comment',    cls: 'dim' }          // dark gray
```


-------------------------------------------------------------------------------------------------------------------

## Design Notes

- Font:IBM Plex Mono (code) + Instrument Serif (headings)
- Theme: Dark terminal, CRT scanline overlay, no external UI libraries
- Animation: CSS transitions for line-by-line code reveal on tab switch; JS `setTimeout` cascade for output simulation
- Layout: CSS Grid split-pane — code on the left, output on the right


-------------------------------------------------------------------------------------------------------------------

## Built With

Vanilla HTML · CSS · JavaScript — no frameworks, no dependencies.
