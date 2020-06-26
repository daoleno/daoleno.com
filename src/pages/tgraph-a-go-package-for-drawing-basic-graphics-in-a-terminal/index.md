---
title: Tgraph - A Go package for drawing basic graphics in a terminal
date: "2020-06-10"
spoiler: Package can draw some basic graphics in a terminal
cta: "react"
---


I just released a go package for drawing basic graphics in a terminal.

https://github.com/daoleno/tgraph

It supports:

- Bar Graphs
- Multi-variable
- Stacked charts
- Emoji

Package can draw some basic graphics in a terminal like this:

```sh
tgraph data2.csv --title "Most Loved Languages"

Most Loved Languages
        Go: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 86.1
    Kotlin: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 67.1
    Python: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 66.7
      Rust: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 62.9
TypeScript: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 62.3
```

An example using emoji:

```sh
tgraph data2.csv --title "Most Loved Languages" --custom-tick 🔥 --width 30

Most Loved Languages
        Go: 🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥 86.1
    Kotlin: 🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥 67.1
    Python: 🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥 66.7
      Rust: 🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥 62.9
TypeScript: 🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥 62.3
```

An example with colors:

```sh
tgraph data1.csv --title "Most Loved/Dreaded Languages" --color red,yellow
```

![color graph](https://dev-to-uploads.s3.amazonaws.com/i/qf9q6ijkoiolyxa3c8ac.png)

An example with stacked:

```sh
tgraph data1.csv --title "Most Loved/Dreaded Languages" --color red,yellow --stacked
```

![stacked graph](https://dev-to-uploads.s3.amazonaws.com/i/qf9q6ijkoiolyxa3c8ac.png)
