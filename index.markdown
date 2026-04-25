---
layout: default
---

<section>
本プロジェクトは、Red Hat Enterprise Linuxクローンを使用した検証の記録である。
よく使うコマンドや設定集を紹介する。
</section>

{% for category in  site.categories %}
## {{ forloop.index }} {{ category[0] }}
{% for post in site.posts reversed %}{% if post.category == category[0] %}1. [{{ index }} {{ post.title }}]({{ site.baseurl }}{{ post.url }})
{% endif %}{% endfor %}{% endfor %}

## 付録

- [コマンド集](https://yumayx.github.io/docs/#commands)
- [プロジェクトレポジトリ](https://github.com/YumaYX/YS910)
