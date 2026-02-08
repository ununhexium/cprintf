
---

###### At the time of writing these lines, Github doesn't support coloring.


You will need to either
* checkout this repository, compile and run the [demo.sh](./demo.sh) script
* check out the Asciinema showcase, but they also have issues with the brighter colors, some styles, ...
* get a better Markdown reader

-----

### Print any string by omitting the format

```bash
cprintf '' 'Whatever you want here!'
```

`Whatever you want here!`

### Print multiple strings by omitting the format

```bash
cprintf '' 'Whatever you want here,' ' and there,' ' and some more..'
```

`Whatever you want here, and there, and some more...`

### Specify a format to use colors with the long or the short notation

```bash
cprintf '{index=1 color=red}+{index=2 color=green}={index=3 color=blue}' 1 2 3
```

```bash
cprintf '{#r}+{#g}={#b}' 1 2 3
```

<pre><span style="color:red;">1</span>+<span style="color:green;">2</span>=<span style="color:blue;">3</span></pre>

### ANSI rainbow

Use either codes, single letters or words to describe a color.

`cprintf '{%1#1}{%1#3}{%1#g}{%1#c}{%1#blue}{%1#magenta}' '█'`

<pre><span style="color:red;">█</span><span style="color:yellow;">█</span><span style="color:green;">█</span><span style="color:cyan;">█</span><span style="color:blue;">█</span><span style="color:magenta;">█</span></pre>

### ANSI bright colors

Shows the color in a brighter variant.

`cprintf '{%1#9}{%1#G}{%1#BLUE}' '█'`

<pre><span style="color:indianred;">█</span><span style="color:chartreuse;">█</span><span style="color:deepskyblue;">█</span></pre>

### Foreground and background colors

```bash
cprintf '{#RED/YELLOW}' 'Warning!'
```

<pre><span style="color:red; background-color: yellow;">Warning!</span></pre>

### Indexed arguments

Change the order of display or re-use a value.

```bash
cprintf '{%3}-{%2}={%1}' a b c
```

`c-b=a`

```bash
cprintf '{%3} {%2} {%1} {%2} {%3}' 1 2 3
```

`3 2 1 2 3`

### Unordered

The specifiers' order is not important

```bash
cprintf '{#red%1}' 'RED'
```
and

```bash
cprintf '{%1#red}' 'RED'
```

Are the same

<pre><span style="color:red;">RED</span></pre>

### Unclutter

If the specifier for an item is getting cluttered, for instance

```bash
cprintf '{#yellow/magenta%1!strikethrough}' 'foo'
```

Take a deep breath, relax, and give yourself some space.
Tabs are accepted.

```bash
cprintf '{ #yellow/magenta   %1   !strikethrough }' 'चक्र'
```

<pre><span style="color:yellow; background-color: magenta; text-decoration: line-through;">चक्र</span></pre>

### New lines and other c-style escape sequences

```bash
cprintf 'a\nb\nc'
```

```
a
b
c
```

### Literal brackets

```bash
cprintf '\{{#cyan}\}' 'value'
```

<pre><span style="color:cyan;">{value}</span></pre>

---

```bash
cprintf '{}' '{}'
```

`{}`

---

```bash
cprintf '\{}'
```

`{}`

### Styles

Bold

```bash
cprintf '{style=bold}' BOLD
```

<pre><b>BOLD</b></pre>

Dimmed

```bash
cprintf '{style=dim}' dimmed
```

<pre><span style="color:dimgray;">dimmed</span></pre>

Italic

```bash
cprintf '{style=italic}' Italic
```

<pre><span style="font-style: italic;">Italic</span></pre>

Underline

```bash
cprintf '{style=underline}' '_-^Underlined^-_'
```

<pre><span style="text-decoration: underline;">_-^Underlined^-_</span></pre>

Blink

This one may not show up as blinking on a web page but it sure blinks in the terminal 🌟

```bash
cprintf '{style=blink}' 'Hey!'
```

<pre><span style="text-decoration: blink;">Hey!</span></pre>

Reversed

The foreground and background specs are inverted.

```bash
cprintf '{style=reverse color=red/yellow}' 'This shows yellow on red instead of red on yellow'
```

<pre><span style="color:yellow; background-color: red;">This shows yellow on red instead of red on yellow</span></pre>

Hidden

```bash
cprintf '->{style=hidden}<-' 'Hide and seek'
```

<pre>-><span style="visibility: hidden;">Hide and seek</span><-</pre>

Strike through

```bash
cprintf '{style=strike color=red}' 'Wrong'
```

<pre><span style="text-decoration: line-through; color: red;">Wrong</span></pre>
