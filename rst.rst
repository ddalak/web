
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

..
  Construction
  ------------
  **Construction**

  ::

    cos

  **Html Output**

  ::
    cos

  **Output**
