---
layout: post
title: Playing with Instructions
---
"[Computer Architecture](https://en.wikipedia.org/wiki/Computer_architecture) is a set of rules and methods that describe ... computer systems" (from Wikipedia). 

Simplifed, an instruction set is  a kind of state machine. When a machine runs instructions like "LOAD" or "STORE", some state changes happend. 

Thanks to [Alex Bradbury](https://twitter.com/asbradbury?lang=en), I got some tools and links to help people get started with with computer architecture. 

One example, is a program that helps to visualise code execution, e.g. [MARS](http://courses.missouristate.edu/KenVollmar/mars/) tried to add some features to help with this  . Another example is  [David White's TMVS](http://david-white.net/tmvs.html) (based on Louden's compiler book).

Now, how can these programs be helpful to make specs like [Risc-V](https://riscv.org/specifications/) better accessible ? One answer might be the [RISC-V simulator](https://github.com/s-macke/jor1k/blob/master/js/worker/riscv/safecpu.js).

<img src="/media/images/workspace_mars_4.png" />
