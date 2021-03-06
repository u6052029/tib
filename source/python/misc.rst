Miscellaneous Python features
=============================

Empty series evaluate to ``False``
----------------------------------

One property of Python builtin series is that if they are empty, then they evaluate to ``False``.

.. jupyter-execute::
    :linenos:

    sample_data = ["some text", ""]
    for text in sample_data:  # yes, lists are iterable too!
        if text:
            print("YES", text)
        else:
            print("NO Empty string")

.. note:: I iterated over elements of the list ``sample_data``. I also used conditionals within the ``for`` loop.

The values ``0```, ``0.0`` and ``None`` also evaluate to ``False``.

.. index:: assert, testing, correctness

Checking correctness using ``assert``
-------------------------------------

**It's essential to check the correctness of your code.** Knowing where and when you do this is a skill that you will develop by programming. For now I just demonstrate the syntax for using the ``assert`` statement.

.. jupyter-execute::
    :linenos:

    name = "Gav"
    assert type(name) == str, "name [%s] is not a string" % name
    print("Sanity check passed!")

This is what it looks like when it fails.

.. jupyter-execute::
    :raises:

    name = 0
    assert type(name) == str, "name [%s] is not a string" % name

.. index::
    pair: list; comprehension
    pair: dict; comprehension

"Comprehensions"
----------------

A comprehension is a very succinct, and simple, ``for`` loop. They are quite fast and are useful.

List comprehensions
^^^^^^^^^^^^^^^^^^^

Here's an example for converting floats into strings.

.. jupyter-execute::
    :linenos:

    nums = [
        0.37756786229607986,
        0.7110011013846619,
        0.349506300557232,
        0.8966182758861486,
    ]
    s = [str(v) for v in nums]
    s

Dictionary comprehensions
^^^^^^^^^^^^^^^^^^^^^^^^^

So many uses for a dict! A simple demonstration, using the ``nums`` variable from above. Notice in this case I'm using multiple unpacking.

.. jupyter-execute::
    :linenos:

    k_v = [["A", 0.1], ["C", 0.2], ["G", 0.3], ["T", 0.4]]
    d = {k: v for k, v in k_v}
    d

.. index:: zip, unzip

Zipping / Unzipping series
--------------------------

Say you have two data series, of equal length, and you want them combined into a single object. This can be done using the built-in `zip()`. For example, here's a ``zip`` operation performed on two strings:

.. jupyter-execute::
    :linenos:

    seq1 = "AGTAATATTGAAGACAAAATATTTGGGAAAACCTATCGGAAGAAGGCAAGCCTCCCCAAC"
    seq2 = "AGTAATACTGAAGACAAAATATTTGGGAAAACCTATCGGAGGAAGGCAAGCCTCCCCAAC"
    columns = list(zip(seq1, seq2))
    columns[:5]

You can also unzip series. For example, consider the following list of lists. We can decompose that into 2 separate series using `zip` with the argument prefaced by ``*``.

.. jupyter-execute::
    :linenos:

    coords = [[0, 23], [42, 42], [13, 27]]
    x, y = zip(*coords)
    x
    y
