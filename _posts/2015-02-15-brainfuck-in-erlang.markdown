---
layout: post
title: "Brainfuck in Erlang"
date: 2015-02-15 12:26:34 +0100
comments: true
categories: programming, erlang
---

Sometime last year, when I started to play around with Erlang, I had the idea of
writing a Brainfuck interpreter in it. Brainfuck is an obscure programming language
which consists of eight instructions. It has no real use, except being a nice
exercice. I wrote most of the interpreter on a weekend, but had some problems
with evaluating Brainfuck loop constructs and left the project laying around
for about eight months.

Last month I sat down and finished the missing parts of the interpreter code.
It is available on [GitHub](https://github.com/nullmedium/erlang-brainfuck-interpreter).

The code is no really perfect. Although it handles nested loops, the loop evaluation
could be improved. Hopefully I will get around fixing those short-comings.
