# MDEx

<!-- MDOC -->

<p align="center">
  <img src="assets/images/mdex_logo.png" width="512" alt="MDEx logo">
</p>

<p align="center">
  A fast 100% CommonMark-compatible GitHub Flavored Markdown parser and formatter for Elixir.
</p>

<p align="center">
  <a href="https://hex.pm/packages/mdex">
    <img alt="Hex Version" src="https://img.shields.io/hexpm/v/mdex">
  </a>

  <a href="https://hexdocs.pm/mdex">
    <img alt="Hex Docs" src="http://img.shields.io/badge/hex.pm-docs-green.svg?style=flat">
  </a>

  <a href="https://opensource.org/licenses/MIT">
    <img alt="MIT" src="https://img.shields.io/hexpm/l/mdex">
  </a>
</p>

## Features

- [Fast](https://github.com/leandrocp/mdex#benchmark)
- Compatible with [CommonMark spec](https://spec.commonmark.org) and [GitHub Flavored Markdown Spec](https://github.github.com/gfm/)
- Binary is precompiled, no need to compile anything

Check out some samples at https://mdex-c31.pages.dev

## Installation

Add `:mdex` dependecy:

```elixir
def deps do
  [
    {:mdex, "~> 0.1"}
  ]
end
```

## Usage

```elixir
Mix.install([{:mdex, "~> 0.1"}])
```

```elixir
MDEx.to_html("# Hello")
#=> "<h1>Hello</h1>\n"
```

```elixir
MDEx.to_html(~S"""
# MDEx

Some benefits you'll find:
- Fast
- CommonMark spec
- Binary is precompiled, no need to compile anything
""") |> IO.puts()
#=>
#=> <h1>MDEx</h1>
#=> <p>Some benefits you'll find:</p>
#=> <ul>
#=> <li>Fast</li>
#=> <li>CommonMark spec</li>
#=> <li>Binary is precompiled, no need to compile anything</li>
#=> <li>Easier to work with since it's Rust</li>
#=> </ul>
```

```elixir
MDEx.to_html(~S"""
# And more...

* Code syntax highlight is also available:

\`\`\`elixir
String.upcase("elixir")
\`\`\`
""") |> IO.puts()
#=> <h1>And more...</h1>
#=> <ul>
#=> <li>Code syntax highlight is also available:</li>
#=> </ul>
#=> <pre class="autumn highlight" style="background-color: #282C34;">
#=> <code class="language-elixir">
#=> <span class="namespace" style="color: #61AFEF;">String</span><span class="operator" style="color: #C678DD;">.</span><span class="function" style="color: #61AFEF;">upcase</span><span class="" style="color: #ABB2BF;">(</span><span class="string" style="color: #98C379;">&quot;elixir&quot;</span><span class="" style="color: #ABB2BF;">)</span>
#=> </code></pre>
```

## Demo and Samples

A [livebook](https://github.com/leandrocp/mdex/blob/main/playground.livemd) and a [script](https://github.com/leandrocp/mdex/blob/main/playground.exs) are available to demo and experiment,
or you can check out all [available samples](https://github.com/leandrocp/mdex/tree/main/priv/generated/samples) at https://mdex-c31.pages.dev

## Benchmark

A [simple script](benchmark.exs) is available to compare existing libs:

```
Name              ips        average  deviation         median         99th %
cmark         24.01 K      0.0417 ms    ±14.11%      0.0405 ms      0.0631 ms
mdex          16.37 K      0.0611 ms     ±9.65%      0.0601 ms      0.0870 ms
md             0.85 K        1.18 ms     ±4.72%        1.16 ms        1.36 ms
earmark        0.47 K        2.14 ms     ±2.82%        2.13 ms        2.42 ms

Comparison:
cmark         24.01 K
mdex          16.37 K - 1.47x slower +0.0194 ms
md             0.85 K - 28.36x slower +1.14 ms
earmark        0.47 K - 51.47x slower +2.10 ms
```

## Motivation

If any of the available libraries are working for you, keep using it, if not then keep reading.

* `earmark` [can't parse](https://github.com/RobertDober/earmark_parser/issues/126) all kinds of documents and is slow to convert hundreds of markdowns.
* `md` is fast enough and extensible but the doc says "If one needs to perfectly parse the common markdown, Md is probably not the correct choice" so it also fails to parse many documents.
* `markdown` is not precompiled and has not received updates in a while.
* `cmark` is a fast CommonMark parser but it requires compiling the C library.

## Looking for help with your Elixir project?

<img src="assets/images/dockyard_logo.png" width="256" alt="DockYard logo">

At DockYard we are [ready to help you build your next Elixir project](https://dockyard.com/phoenix-consulting).
We have a unique expertise in Elixir and Phoenix development that is unmatched and we love to [write about Elixir](https://dockyard.com/blog/categories/elixir).

Have a project in mind? [Get in touch](https://dockyard.com/contact/hire-us)!

## Acknowledgements

* Use Rust's [comrak crate](https://crates.io/crates/comrak) under the hood.
* [Logo](https://www.flaticon.com/free-icons/rpg) created by by Freepik - Flaticon
* [Logo font](https://github.com/quoteunquoteapps/CourierPrime) designed by [Alan Greene](https://github.com/a-dg)
