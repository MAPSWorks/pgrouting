..
   ****************************************************************************
    pgRouting Manual
    Copyright(c) pgRouting Contributors

    This documentation is licensed under a Creative Commons Attribution-Share
    Alike 3.0 License: http://creativecommons.org/licenses/by-sa/3.0/
   ****************************************************************************


.. _pgr_edmondsKarp:

pgr_edmondsKarp - Proposed
============================================


Synopsis
-------------------------------------------------------------------------------

``pgr_edmondsKarp`` — Calculates the flow on the graph edges that maximizes the flow from the sources to the targets using Push Relabel Algorithm.


.. figure:: images/boost-inside.jpeg
   :target: http://www.boost.org/libs/graph/doc/push_relabel_max_flow.html

   Boost Graph Inside

.. Rubric:: Availability:

* Renamed 2.5.0, Previous name pgr_maxFlowEdmondsKarp
* New in 2.3.0

.. include:: proposed.rst
   :start-after: begin-warn-expr
   :end-before: end-warn-expr


.. include::  flow-family.rst
    :start-after: characteristics_start
    :end-before: characteristics_end

* Running time: :math:`O( V * E ^ 2)`

Signature Summary
-----------------

.. code-block:: none

    pgr_edmondsKarp(edges_sql, source,  target) - Proposed
    pgr_edmondsKarp(edges_sql, sources, target) - Proposed
    pgr_edmondsKarp(edges_sql, source,  targets) - Proposed
    pgr_edmondsKarp(edges_sql, sources, targets) - Proposed
    RETURNS SET OF (seq, edge, start_vid, end_vid, flow, residual_capacity)
    OR EMPTY SET



.. index::
    single: edmondsKarp(One to One) - Proposed

One to One
.....................................................................

Calculates the flow on the graph edges that maximizes the flow from the `source` to the `target`.

.. code-block:: none

    pgr_edmondsKarp(edges_sql, source,  target)
    RETURNS SET OF (seq, edge, start_vid, end_vid, flow, residual_capacity)
    OR EMPTY SET

:Example:

.. literalinclude:: doc-pgr_edmondsKarp.queries
   :start-after: -- q1
   :end-before: -- q2


.. index::
    single: edmondsKarp(One to Many) - Proposed

One to Many
.....................................................................

Calculates the flow on the graph edges that maximizes the flow from the `source` to all of the `targets`.

.. code-block:: none

    pgr_edmondsKarp(edges_sql, source,  targets)
    RETURNS SET OF (seq, edge, start_vid, end_vid, flow, residual_capacity)
    OR EMPTY SET

:Example:

.. literalinclude:: doc-pgr_edmondsKarp.queries
   :start-after: -- q2
   :end-before: -- q3


.. index::
    single: edmondsKarp(Many to One) - Proposed

Many to One
.....................................................................

Calculates the flow on the graph edges that maximizes the flow from all of the `sources` to the `target`.

.. code-block:: none

    pgr_edmondsKarp(edges_sql, sources,  target)
    RETURNS SET OF (seq, edge, start_vid, end_vid, flow, residual_capacity)
    OR EMPTY SET

:Example:

.. literalinclude:: doc-pgr_edmondsKarp.queries
   :start-after: -- q3
   :end-before: -- q4


.. index::
    single: edmondsKarp(Many to Many) - Proposed

Many to Many
.....................................................................

Calculates the flow on the graph edges that maximizes the flow from all of the `sources` to all of the `targets`.

.. code-block:: none

    pgr_edmondsKarp(edges_sql, sources,  targets)
    RETURNS SET OF (seq, edge, start_vid, end_vid, flow, residual_capacity)
    OR EMPTY SET

:Example:

.. literalinclude:: doc-pgr_edmondsKarp.queries
   :start-after: -- q4
   :end-before: -- q5

Description of the Signatures
--------------------------------------------------------

.. include:: pgRouting-concepts.rst
    :start-after: flow_edges_sql_start
    :end-before: flow_edges_sql_end


.. include::  ./pgr_maxFlow.rst
    :start-after: pgr_flow_parameters_start
    :end-before: pgr_flow_parameters_end


.. include:: pgRouting-concepts.rst
    :start-after: result_flow_start
    :end-before: result_flow_end


See Also
--------

* :ref:`maxFlow`, :ref:`pgr_boykovKolmogorov <pgr_boykovKolmogorov>`, :ref:`pgr_PushRelabel <pgr_pushRelabel>`
* http://www.boost.org/libs/graph/doc/edmonds_karp_max_flow.html
* https://en.wikipedia.org/wiki/Edmonds%E2%80%93Karp_algorithm

.. rubric:: Indices and tables

* :ref:`genindex`
* :ref:`search`

