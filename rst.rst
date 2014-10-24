
reStructuredText overview
=========================

This examples are from http://sphinx-doc.org/rest.html#rst-primer and  http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html.

Some may be identical some may be modified.


Section
--------

**Construction**

::

  section
  =======  

**Html**

::

  <div class="section" id="id1">
  <h1>section<a class="headerlink" href="#id1" title="Permalink to this headline">¶</a></h1>
       
**Output**

section
=======

Bold text
----------
**Construction**

::

  This is **bold**

**Html Output**

::

  This is <strong>bold</strong>

**Output**

This is **bold**

Interpreted Text
----------------
**Construction**

::

  This is `interpreted text`.

**Output**

This is `interpreted text`.

Emphasized text
---------------
**Construction**

::

  This is *emphasized text*.

**Output**

This is *emphasized text*.

Inline literals
---------------
**Construction**

::

  This text is an example of ``inline literals``.

**Output**

This text is an example of ``inline literals``.

List
----
**Construction**

::

  * This is a bulleted list.
  * It has two items, the second
    item uses two lines.

  1. This is a numbered list.
  2. It has two items too.

  #. This is a numbered list.
  #. It has two items too.

**Html Output**

::

  TODO

**Output**

* This is a bulleted list.
* It has two items, the second
  item uses two lines.

1. This is a numbered list.
2. It has two items too.

#. This is a numbered list.
#. It has two items too.

..
  Construction
  ------------
  **Construction**

  ::

    TODO

  **Html Output**

  ::

    TODO

  **Output**
