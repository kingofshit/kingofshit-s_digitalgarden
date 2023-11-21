---
{"dg-publish":true,"permalink":"/template/zotero模板/","dgPassFrontmatter":true}
---

# 文献信息
## DOI
{{DOI}}

## 标题
{{title}}

## 作者
{% for t in creators %}{{t.firstName}} {{t.lastName}}{{t.name}}{% if not loop.last %}, {% endif %}{% endfor %}

## 时间
{{date | format("YYYY-MM-DD")}}

## 摘要
{{abstractNote}}

# 注释

{% for annotation in annotations %}
{% if annotation.colorCategory == "Yellow" %}## {{annotation.comment}}{% endif %}
{% if annotation.colorCategory == "Green" %} ### 翻译
{{annotation.comment}}
{{annotation.annotatedText}}{% endif %}
{{pdfZoteroLink|replace("//select/", "//open-pdf/")|replace(")", "")}}?page={{annotation.page}}&annotation={{annotation.id}})
{% endfor %}