Pending Release Notes
=====================

Updates / New Features
----------------------

* Bumped ``numpy`` floor to ``>=2.0`` on all supported Python versions, and
  to ``>=2.3.0`` on Python 3.14.

* Added a ``scipy >= 1.16.2`` requirement on Python 3.14.

* Added ``torch >= 2.10.0``, ``torchvision >= 0.25.0``,
  ``scikit-learn >= 1.7.2``, and ``scikit-image >= 0.26.0`` dev requirements
  on Python 3.14.

Fixes
-----

* Fixed pickling error of ``Dataset`` helpers in
  ``tests/test_per_worker_seed.py`` by moving them to module scope, required
  under Python 3.14's ``forkserver`` default for the Linux multiprocessing
  start method.

* Updated ``tests/functional/test_functional.py::test_scale`` to use
  ``np.testing.assert_allclose(..., atol=1)`` to support the ``INTER_LINEAR``
  rounding shift introduced in OpenCV 4.13.
