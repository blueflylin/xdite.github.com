--- 
title: Pow + Gollum
layout: post
---


[Gollum](https://github.com/github/gollum) 是 Github [將他們的 wiki opensource 後再製](https://github.com/blog/699-making-github-more-open-git-backed-wikis) 的產品，一言以蔽之：git-backend wiki。

原先 release 出來的版本，只能藉由 http server 跑在單一 port。如果想自己用 mod_rails 跑在 apache 上，需要寫大量的 dirty hack，結果還不一定 work。（gollum 剛出來時我就真的這樣幹了…)
剛剛想寫一點技術文章，又去把 Gollum 翻出來。弄一弄，發現翻到最新的解法還是不一定 work。

本來想放棄了。不過後來發現了 "Pow" 。

[Pow](http://pow.cx/) 是 37 Signals opensource 出來的一套 Rack Server。其標榜的就是 **Zero Config**。不用寫任何 config 的 rack server。

利用 firewall rule 把 traffic 都導回 \*.dev 。只要把 project symlink 到 ~/.pow 下，就可以直接把 project 開起來了..。
config 和 /etc/hosts 這種東西根本都不用改…

這意謂著我可以把 Gollum 透過 Pow 架設起來。直接變成 http://wiki.dev。

以下是 gollum 需要的 config.ru

<pre>
require 'rubygems'
require "gollum/frontend/app"

Precious::App.set(:gollum_path, File.dirname(__FILE__))
Precious::App.set(:wiki_options, {})
run Precious::App

</pre>
