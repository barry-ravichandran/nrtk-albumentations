Pending Release Notes
=====================

Updates / New Features
----------------------

* Added Python 3.14 to the supported version range and CI test matrix. The
  runtime ``numpy`` floor was raised from ``>=1.26`` to ``>=2.0`` across all
  supported Python versions; Python 3.14 additionally requires
  ``numpy>=2.3.0`` to avoid a ``numpy.testing.assert_array_almost_equal``
  regression in numpy 2.2.x (see `matplotlib/matplotlib#29959
  <https://github.com/matplotlib/matplotlib/issues/29959>`_). Python 3.14
  also pins ``scipy>=1.16.2`` (runtime), and ``torch>=2.10.0`` /
  ``torchvision>=0.25.0`` / ``scikit-learn>=1.7.2`` / ``scikit-image>=0.26.0``
  (dev) — the lowest versions with cp314 wheels available across Linux,
  macOS, and Windows. ``scipy`` and dev dependency pins are unchanged for
  Python <3.14.

Fixes
-----

* Moved the ``Dataset`` helpers in ``tests/test_per_worker_seed.py`` to module
  scope so they remain picklable under Python 3.14's new ``forkserver`` default
  for the Linux multiprocessing start method. Without this, the DataLoader
  workers in ``test_worker_seed_with_torch`` and
  ``test_dataloader_epoch_diversity`` raised ``PicklingError`` on locally
  defined classes.

* Relaxed ``tests/functional/test_functional.py::test_scale`` to use
  ``np.testing.assert_allclose(..., atol=1)`` instead of strict element
  equality. OpenCV 4.13 changed ``INTER_LINEAR`` rounding for uint8 inputs,
  shifting a few output pixels by ±1; the previous exact-equality assertion
  forced an ``opencv-python-headless<4.13`` dev pin. With the relaxed
  tolerance the cap has been dropped and the dev dependency tracks the latest
  release.
