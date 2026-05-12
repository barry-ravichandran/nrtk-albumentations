Pending Release Notes
=====================

Updates / New Features
----------------------

* Replaced ``simsimd`` dependency with ``numkong``.

Breaking Changes
----------------

* The public helpers ``add_weighted_simsimd``, ``add_array_simsimd``, ``multiply_by_constant_simsimd``, and ``add_constant_simsimd`` in ``albucore.functions`` have been replaced by private ``_*_numkong`` equivalents. The old names are retained as deprecated aliases for one release and emit a ``DeprecationWarning`` when called; downstream callers should migrate to the public ``add_weighted`` dispatcher instead.

Fixes
-----

* Worked around a macOS-arm64 segfault during the test suite caused by duplicate ``libomp`` runtimes shipped by ``numkong`` and ``torch`` by setting ``OMP_NUM_THREADS=1`` on the macOS CI job.
