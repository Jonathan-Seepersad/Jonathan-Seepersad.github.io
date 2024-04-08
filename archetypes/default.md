---
title: '{{ replace .File.ContentBaseName "-" " " | title }}'
date: {{ .Date }}
draft: true
description: ""
{{ if not (eq .Site.Author.name "")}}author: "{{ .Site.Author.name }}"{{ end }}
keywords: []
---
