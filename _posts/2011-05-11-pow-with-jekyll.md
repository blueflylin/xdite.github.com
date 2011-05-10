--- 
title: Pow + Jekyll
layout: post
---

[Jekyll](https://github.com/mojombo/jekyll) 是一套輕量級的 Blog 系統。現在有不少 Hacker 使用 Jekyll 撰寫他們的技術 blog。

最近我在整理自己曾經寫的文章，鑑於 Wordpress 實在是不好貼 code。況且也在練習 [Markdown](http://markdown.tw/) 與 [Textile](http://en.wikipedia.org/wiki/Textile_(markup_language) 這種 markup 。

於是就想到用 [Jekyll](https://github.com/mojombo/jekyll)  整理曾經發表過的文章。

因為上次使用過 Pow + Gollum 的組合，這次嘗試著也用 Pow + Jekyll 架站。

所需要安裝的 gem 是 [rack-jekyll](https://github.com/bry4n/rack-jekyll)

<pre>
  gem install rack-jekyll
</pre>

另外我寫了需要的 Gemfile 以及 config.ru

**Gemfile**

<pre>
gem "rack-jekyll", :require => "rack/jekyll"
</pre>

**config.ru**

<pre>
require "rubygems"
require "rack/jekyll"
require "yaml"
run Rack::Jekyll.new
</pre>

<hr>
因為 Markdown 實在不太夠用，其實我還用了 [Maruku](https://github.com/nex3/maruku)。

