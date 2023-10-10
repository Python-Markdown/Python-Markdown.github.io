title:      Release Notes for v2.4

Python-Markdown 2.4 Release Notes
=================================

We are pleased to release Python-Markdown 2.4 which adds one new extension
and fixes various bugs. See the list of changes below for details.

Python-Markdown supports Python versions 2.6, 2.7, 3.1, 3.2, and 3.3.

Backwards-incompatible Changes
------------------------------

* The `force_linenos` configuration setting of the CodeHilite extension has been
  marked as **Deprecated**. It had previously been marked as "Pending
  Deprecation" in version 2.3 when a new setting `linenums` was added to replace
  it. See documentation for the [CodeHilite Extension] for an explanation of the
  new `linenums` setting. The new setting will honor the old `force_linenos` if
  it is set, but `force_linenos` will raise a `DeprecationWarning` and will
  likely be removed in a future version of Python-Markdown.

[CodeHilite Extension]: ../extensions/code_hilite.md

* URLs are no longer percent-encoded. This improves compatibility with the
  original (written in Perl) Markdown implementation. Please percent-encode your
  URLs manually when needed.

What's New in Python-Markdown 2.4
---------------------------------

* Thanks to the hard work of [Dmitry Shachnev] the [Smarty Extension] has been
  added, which implements [SmartyPants] using Python-Markdown's Extension API.
  This offers a few benefits over a third party script. The HTML does not need
  to be "tokenized" twice, no hacks are required to combine SmartyPants and code
  highlighting, and we get markdown's escaping feature for free. Please try it
  out and report bugs and/or improvements.

[Dmitry Shachnev]: https://github.com/mitya57
[Smarty Extension]: ../extensions/smarty.md
[SmartyPants]: https://daringfireball.net/projects/smartypants/

* The [Table of Contents Extension] now supports new `permalink` option for
  creating [Sphinx]-style anchor links.

[Table of Contents Extension]: ../extensions/toc.md
[Sphinx]: http://sphinx-doc.org/

* It is now possible to enable Markdown formatting inside HTML blocks by
  appending `markdown=1` to opening tag attributes. See [Markdown Inside HTML
  Blocks] section for details. Thanks to [ryneeverett] for implementing this
  feature.

[Markdown Inside HTML Blocks]: ../extensions/extra.md#nested-markdown-inside-html-blocks
[ryneeverett]: https://github.com/ryneeverett

* The code blocks now support emphasizing some of the code lines. To use this
  feature, specify `hl_lines` option after language name, for example (using the
  [Fenced Code Extension]):

        ```.python hl_lines="1 3"
        # This line will be emphasized.
        # This one won't.
        # This one will be also emphasized.
        ```

    Thanks to [A. Jesse Jiryu Davis] for implementing this feature.

[Fenced Code Extension]: ../extensions/fenced_code_blocks.md
[A. Jesse Jiryu Davis]: https://github.com/ajdavis

* Various bug fixes have been made. See the [commit
  log](https://github.com/Python-Markdown/markdown/commits/master) for a
  complete history of the changes.
