CJKwrap
=======

**This is a Python 3 only version of CJKwrap**

**CJKwrap** is a library for wrapping and filling CJK text.

CJKwrap is developed by Florent Gallaire fgallaire@gmail.com.

Usage
-----

``is_wide()`` to know if a char is double-width, ``cjklen()`` and ``cjkslices()`` to replace built-in ``len()`` and slicing::

    >>> import cjkwrap
    >>> cjkwrap.is_wide("c")
    False
    >>> cjkwrap.is_wide("長")
    True
    >>> cjkwrap.cjklen("最終的には良い長さ")
    18
    >>> head, tail = cjkwrap.cjkslices("最終的には良い長さ", 6)
    >>> print(head)
    最終的
    >>> print(tail)
    には良い長さ

As ``cjklen()`` uses ``len()`` for non unicode stuff, you can safely do this::

    >>> from cjkwrap import cjklen as len
    >>> len("最終的には良い長さ")
    18
    >>> len([1, 2, 3, 4])
    4

``wrap()`` and ``fill()`` to replace the ones from the Python standard library::

    >>> wrapped_cjk = cjkwrap.wrap("最終的に良いラッピング", 10)
    >>> for line in wrapped_cjk: print(line)
    ... 
    最終的に良
    いラッピン
    グ
    >>> print(cjkwrap.fill("最終的に良いラッピング", 10))
    最終的に良
    いラッピン
    グ

Mixed content is allowed::

    >>> cjkwrap.cjklen("CJK 最終的には良い長さ")
    22
    >>> print(cjkwrap.fill("CJK 最終的には良い長さ", 10))
    CJK 最終的
    には良い長
    さ

License
-------

CJKwrap codebase from textwrap by Greg Ward (gward@python.net) under the Python license.
