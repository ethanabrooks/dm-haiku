:github_url: https://github.com/deepmind/dm-haiku/tree/master/docs

Haiku Documentation
===================

Haiku is a library built on top of JAX designed to provide simple, composable
abstractions for machine learning research.

.. code-block:: python

    import haiku as hk
    import jax
    import jax.numpy as jnp

    def forward(x):
      mlp = hk.nets.MLP([300, 100, 10])
      return mlp(x)

    forward = hk.transform(forward)

    rng = jax.random.PRNGKey(42)
    x = jnp.ones([8, 28 * 28])
    params = forward.init(rng, x)
    logits = forward.apply(params, rng, x)

Installation
------------

See https://github.com/google/jax#pip-installation for instructions on
installing JAX.

We suggest installing the latest version of Haiku by running::

    $ pip install git+https://github.com/deepmind/dm-haiku
    
Alternatively, you can install via PyPI::

    $ pip install -U dm-haiku

.. toctree::
   :caption: Guides
   :maxdepth: 1

   notebooks/basics
   notebooks/transforms

.. toctree::
   :caption: API Documentation
   :maxdepth: 1

   api

.. toctree::
   :caption: Advanced
   :maxdepth: 1

   notebooks/jax2tf
   notebooks/build_your_own_haiku
   notebooks/visualization
   notebooks/non_trainable

Known issues
------------

.. warning::
    Using JAX transformations like :func:`jax.jit` and :func:`jax.remat` inside
    of Haiku networks can lead to hard to interpret tracing errors and
    potentially silently wrong results. Read :doc:`notebooks/transforms` to find
    out how to work around these issues.

Contribute
----------

- Issue tracker: https://github.com/deepmind/dm-haiku/issues
- Source code: https://github.com/deepmind/dm-haiku/tree/master

Support
-------

If you are having issues, please let us know by filing an issue on our
`issue tracker <https://github.com/deepmind/dm-haiku/issues>`_.

License
-------

Haiku is licensed under the Apache 2.0 License.

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
