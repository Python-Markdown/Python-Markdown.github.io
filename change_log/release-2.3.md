title: Release Notes for v2.3

Python-Markdown 2.3 Release Notes
=================================

We are pleased to release Python-Markdown 2.3 which adds one new extension,
removes a few old (obsolete) extensions, and now runs on both Python 2 and
Python 3 without running the 2to3 conversion tool. See the list of changes
below for details.

Python-Markdown supports Python versions 2.6, 2.7, 3.1, 3.2, and 3.3.

Backwards-incompatible Changes
------------------------------

* Support has been dropped for Python 2.5. No guarantees are made that the
  library will work in any version of Python lower than 2.6. As all supported
  Python versions include the ElementTree library, Python-Markdown will no
  longer try to import a third-party installation of ElementTree.

* All classes are now "new-style" classes. In other words, all classes subclass
  from 'object'. While this is not likely to affect most users, extension
  authors may need to make a few minor adjustments to their code.

* "safe_mode" has been further restricted. Markdown formatted links must be of a
  known white-listed scheme when in "safe_mode" or the URL is discarded. The
  white-listed schemes are: 'HTTP', 'HTTPS', 'FTP', 'FTPS', 'MAILTO', and
  'news'. Schemeless URLs are also permitted, but are checked in other ways - as
  they have been for some time.

* The ids assigned to footnotes now contain a dash (`-`) rather than a colon
  (`:`) when `output_format` it set to `"html5"` or `"xhtml5"`. If you are
  making reference to those ids in your JavaScript or CSS and using the HTML5
  output, you will need to update your code accordingly. No changes are
  necessary if you are outputting XHTML (the default) or HTML4.

* The `force_linenos` configuration setting of the CodeHilite extension has been
  marked as **Pending Deprecation** and a new setting `linenums` has been added
  to replace it. See documentation for the [CodeHilite Extension] for an
  explanation of the new `linenums` setting. The new setting will honor the old
  `force_linenos` if it is set, but it will raise a `PendingDeprecationWarning`
  and will likely be removed in a future version of Python-Markdown.

[CodeHilite Extension]: ../extensions/code_hilite.md

* The "RSS" extension has been removed and no longer ships with Python-Markdown.
  If you would like to continue using the extension (not recommended), it is
  archived on [GitHub](https://gist.github.com/waylan/4773365).

* The "HTML Tidy" Extension has been removed and no longer ships with
  Python-Markdown. If you would like to continue using the extension (not
  recommended), it is archived on
  [GitHub](https://gist.github.com/waylan/5152650). Note that the underlying
  library, uTidylib, is not Python 3 compatible. Instead, it is recommended that
  the newer [PyTidyLib] (version 0.2.2+ for Python 3 comparability - install
  from GitHub not PyPI) be used. As the API for that library is rather simple,
  it is recommended that the output of Markdown be wrapped in a call to
  PyTidyLib rather than using an extension (for example:
  `tidylib.tidy_fragment(markdown.markdown(source), options={...})`).

[PyTidyLib]: http://countergram.github.io/pytidylib/

What's New in Python-Markdown 2.3
---------------------------------

* The entire code base now universally runs in Python 2 and Python 3 without any
  need for running the 2to3 conversion tool. This not only simplifies testing,
  but by using Unicode_literals, results in more consistent behavior across
  Python versions. Additionally, the relative imports (made possible in Python 2
  via absolute_import) allows the entire library to more easily be embedded in a
  sub-directory of another project. The various files within the library will
  still import each other properly even though 'markdown' may not be in Python's
  root namespace.

* The [Admonition Extension] has been added, which implements [rST-style][rST]
  admonitions in the Markdown syntax. However, be warned that this extension is
  experimental and the syntax and behavior is still subject to change. Please
  try it out and report bugs and/or improvements.

[Admonition Extension]: ../extensions/admonition.md
[rST]: http://docutils.sourceforge.net/docs/ref/rst/directives.html#specific-admonitions

* Various bug fixes have been made. See the [commit
  log](https://github.com/Python-Markdown/markdown/commits/master) for a
  complete history of the changes.
