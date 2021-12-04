---
title: '`tex-html` の使い方・記法'
---

## 使い方

```
tex-html input.md -o output.html
```

## 記法

基本的な書き方は普通のMarkdownと同じです。普通のMarkdownと違うところを紹介します。

### $\LaTeX$ による数式
Markdown:

```
$$
f'\left(x\right)=\lim_{\Delta x\to0}\frac{f\left(x+\Delta x\right)-f\left(x\right)}{\Delta x}
$$
```

表示:

$$
f'\left(x\right)=\lim_{\Delta x\to0}\frac{f\left(x+\Delta x\right)-f\left(x\right)}{\Delta x}
$$

### AsciiMath による数式
Markdown:

```
$$:a
f'(x)=lim_{Delta x->0}(f(x+Delta x)-f(x))/(Delta x)
$$
```

表示

$$:a
f'(x)=lim_{Delta x->0}(f(x+Delta x)-f(x))/(Delta x)
$$

### 数式を参照する
Markdown

```
[@eq:equation1] は微分の定義です。

$$:a
f'(x)=lim_{Δx->0}(f(x+Δx)-f(x))/(Δx)
$${#eq:equation1}
```

表示:

[@eq:equation1] は微分の定義です。

$$:a
f'(x)=lim_{Δx->0}(f(x+Δx)-f(x))/(Δx)
$${#eq:equation1}


### コードブロック
Markdown:

````md
```ruby
#!/usr/bin/env ruby

if ARGV[0] == '--help' || ARGV[0] == '-h' then
    puts "Usage: #{$0} <input.md >output.html"
else
    system("pandoc -d \'#{__dir__}/../pandoc-defaults.yaml\' --template \'#{__dir__}/../tex-html-template.html\' #{ARGV.join(' ')}")
end
```
````

表示:
```ruby
#!/usr/bin/env ruby

if ARGV[0] == '--help' || ARGV[0] == '-h' then
    puts "Usage: #{$0} <input.md >output.html"
else
    system("pandoc -d \'#{__dir__}/../pandoc-defaults.yaml\' --template \'#{__dir__}/../tex-html-template.html\' #{ARGV.join(' ')}")
end
```



### 行番号やキャプションをつけたコードブロック{.next-page}

```{.ruby .numberLines caption="tex-html"}
#!/usr/bin/env ruby

if ARGV[0] == '--help' || ARGV[0] == '-h' then
    puts "Usage: #{$0} <input.md >output.html"
else
    system("pandoc -d \'#{__dir__}/../pandoc-defaults.yaml\' --template \'#{__dir__}/../tex-html-template.html\' #{ARGV.join(' ')}")
end
```

````md
```{.ruby .numberLines caption="tex-html"}
#!/usr/bin/env ruby

if ARGV[0] == '--help' || ARGV[0] == '-h' then
    puts "Usage: #{$0} <input.md >output.html"
else
    system("pandoc -d \'#{__dir__}/../pandoc-defaults.yaml\' --template \'#{__dir__}/../tex-html-template.html\' #{ARGV.join(' ')}")
end
```
````

### 注釈

注釈も書けます。[これは注釈です。]{.footnote}

```md
注釈も書けます。[これは注釈です。]{.footnote}
```

### 表
[@tbl:table1]は、表です。


| AsciiMath  |          $\LaTeX$           |     表示      |
| :--------: | :-------------------------: | :-----------: |
|   `a/b`    |         `\frac ab`          |   $:a a/b$    |
|   `ab/c`   |         `a\frac bc`         |   $:a ab/c$   |
|  `(ab)/c`  |        `\frac{ab}c`         |  $:a (ab)/c$  |
| `log(a/b)` | `\log\left(\frac ab\right)` | $:a log(a/b)$ |
|   `1pm2`   |           `1\pm2`           |   $:a 1pm2$   |
|  `cos a`   |          `\cos a`           |  $:a cos a$   |
:AsciiMath と $\LaTeX$ の比較 {#tbl:table1}

### 見出し
見出しは、`##` から始めてください。`h1` はタイトルに使われます。

