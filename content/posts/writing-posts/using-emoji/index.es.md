---
title: "Usando Emojis"
date: 2020-06-08T06:15:25+06:00
author:
  name: BernatBC
  image: images/author/bernatbc.png
menu:
  sidebar:
    name: Usando Emojis
    identifier: writing-post-using-emoji
    parent: writing-post
    weight: 60
---

Los emojis se pueden habilitar a un proyecto de Hugo de distintas formas.
<!--more-->
La función [`emojify`](https://gohugo.io/functions/emojify/) se puede llamar directamente a las plantillas o a los [Inline Shortcodes](https://gohugo.io/templates/shortcode-templates/#inline-shortcodes).

Para habilitar los emojis globalmente, establece `enableEmoji` a `true` en el archivo `config.yaml` y después puedes escribir los códigos de los emojis directamente en archivos de contenido; por ejemplo. Más información [aquí](https://gohugo.io/getting-started/configuration/).


<p><span class="nowrap"><span class="emojify">🙈</span> <code>:see_no_evil:</code></span>  <span class="nowrap"><span class="emojify">🙉</span> <code>:hear_no_evil:</code></span>  <span class="nowrap"><span class="emojify">🙊</span> <code>:speak_no_evil:</code></span></p>
<br>

El [Emoji cheat sheet](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md) es una referencia útil para códigos de emojis.

***

**NÓTESE BIEN.** Los pasos anteriores habilitan secuencias y caracteres emoji estándar Unicode en Hugo; sin embargo, la representación de estos glifos depende del navegador y la plataforma. Para darle estilo al emoji, puedes usar una fuente de emoji de terceros o una pila de fuentes; por ejemplo.

{{< highlight html >}}
.emoji {
font-family: Apple Color Emoji,Segoe UI Emoji,NotoColorEmoji,Segoe UI Symbol,Android Emoji,EmojiSymbols;
}
{{< /highlight >}}

{{< css.inline >}}
<style>
.emojify {
	font-family: Apple Color Emoji,Segoe UI Emoji,NotoColorEmoji,Segoe UI Symbol,Android Emoji,EmojiSymbols;
	font-size: 2rem;
	vertical-align: middle;
}
@media screen and (max-width:650px) {
    .nowrap {
	display: block;
	margin: 25px 0;
}
}
</style>
{{< /css.inline >}}

