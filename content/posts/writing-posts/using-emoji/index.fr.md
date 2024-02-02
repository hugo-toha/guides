---
title: "Utilisation d'Emoji"
date: 2020-06-08T06:15:25+06:00
author:
  name: Nicolas Dietlin
  image: images/author/nicolas.jpg
menu:
  sidebar:
    name: Utilisation d'Emoji
    identifier: writing-post-using-emoji
    parent: writing-post
    weight: 60
---

Emoji peut être activé dans un projet Hugo de plusieurs façons.
<!--more-->
La fonction [`emojify`](https://gohugo.io/functions/emojify/) peut être appelée directement dans les templates ou par [shortcodes en ligne](https://gohugo.io/templates/shortcode-templates/#inline-shortcodes).

Pour activer globallement Emoji, paramètrez `enableEmoji` à `true` dans la [configuration](https://gohugo.io/getting-started/configuration/) de votre site et vous pouvez ensuite taper des codes raccourcis d'Emoji directement dans les contenus de vos fichiers; par exemple:

<p><span class="nowrap"><span class="emojify">🙈</span> <code>:see_no_evil:</code></span>  <span class="nowrap"><span class="emojify">🙉</span> <code>:hear_no_evil:</code></span>  <span class="nowrap"><span class="emojify">🙊</span> <code>:speak_no_evil:</code></span></p>
<br>

L'[aide mémoire Emoji](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md) est une référence utile pour les codes emoji.

***

**N.B.** Les étapes ci-dessus active les caractères Unicode Standard Emoji dans Hugo, cepandant, le rendu de ces glyphes dépend du navigateur et de la plateforme. Pour styler l'emoji vous pouvez utiliser une police emoji tierce ou un empilement de polices; par exemple:

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

