---
title: Asciinema
menu:
  sidebar:
    name: Asciinema
    identifier: asciinema
    parent: linux
    weight: 300
---

- Figured out how to embed Asciicast directly on my site by using my own shortcode.

  - Made a directory 'Shortcodes' under 'Layouts' section of my Hugo site.
  
  - Created a file **asciinema.html** in the same and wrote the shortcode there.
  `<script src="https://asciinema.org/a/{{.Get 0}}.js" id="asciicast-{{.Get 0}}" async></script>`
  
  - Now the asciicast could be directly embedded in Hugo site by writing `{{follow the syntax given below}}` in the markdown file.
  Suppose for **https://asciinema.org/a/I4VLffwlrXJH1r7iooQ4vzX5e** , the synatx would be `<asciinema I4VLffwlrXJH1r7iooQ4vzX5e>`.
  {{<asciinema I4VLffwlrXJH1r7iooQ4vzX5e>}}