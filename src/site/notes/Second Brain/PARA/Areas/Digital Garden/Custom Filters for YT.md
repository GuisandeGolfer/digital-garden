---
{"dg-publish":true,"dg-path":"Areas/Digital Garden/Custom Filters for YT.md","permalink":"/areas/digital-garden/custom-filters-for-yt/","created":"2024-09-02T19:03:49.874-07:00","updated":"2024-09-02T19:04:36.618-07:00"}
---

>[!anchor] regex

!\[(.*)\]\(https?:\/\/w*\.?(?:(?:youtu\.be\/)|(?:youtube\.com\/watch\?v=))(.*)\)

>[!award] Output
><iframe src="https://www.youtube.com/embed/$2" title="$1" style="width:100%; aspect-ratio:16/9" loading="lazy" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
 