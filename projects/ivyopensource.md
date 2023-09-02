---
layout: project
type: project
image: img/unify_ivy_logo.png
title: "Unify AI/Ivy Open Source"
date: 2023
published: true
labels:
  - Open Source  
  - Artificial Intelligience
  - Python
summary: "My contributions to UnifyAI's Ivy repository."
---

<div class="text-center p-4">
  <img width="200px" src="../img/unifyai_logo_full.png" class="img-thumbnail" >
  <img width="200px" src="../img/numpy-logo.png" class="img-thumbnail" >
  <img width="200px" src="../img/jax_logo.png" class="img-thumbnail" >
</div>

This contribution adds significant value to the open-source repository by bridging the gap between the popular NumPy library and JAX, a powerful library for numerical computing with GPU acceleration and automatic differentiation capabilities. NumPy is widely used for scientific and numerical computing tasks, and its FFT functions are integral to many applications. However, JAX offers improved performance and GPU support, making it increasingly attractive for machine learning and scientific computing. By providing a JAX-compatible FFT function that mirrors NumPy's API, this contribution enhances the accessibility and adoption of JAX among developers who are already familiar with NumPy, thereby expanding the user base and potential contributors to the open-source project.

Furthermore, this contribution aligns with the open-source philosophy of collaboration and community-driven development. It ensures that users can seamlessly transition from NumPy to JAX while preserving their existing codebase, reducing the friction associated with adopting new libraries. This improved interoperability not only benefits current users but also encourages the broader open-source community to explore the capabilities of JAX for their numerical computing needs. In doing so, this contribution strengthens the project's ecosystem and fosters a more inclusive and vibrant community around JAX, ultimately enhancing its standing as a valuable tool in the open-source software landscape.

Overall, this code defines a JAX-compatible version of the FFT function that wraps JAX's internal FFT core computation function while maintaining a similar signature to NumPy's np.fft.fft function for ease of use and compatibility. It is part of a larger codebase that seems to include additional functions and modules related to FFT and linear algebra operations.

```python
# flake8: noqa
from typing import Optional

import numpy as np
from etils.array_types import ArrayLike, Array
from jax._src.numpy.fft import _fft_core_1d
from jax._src.numpy.util import _wraps
from jaxlib import xla_client

from . import fft
from . import linalg
from . import name_space_functions
from .name_space_functions import *


@_wraps(np.fft.fft)
def fft(a: ArrayLike, n: Optional[int] = None,
        axis: int = -1, norm: Optional[str] = None) -> Array:
    return _fft_core_1d('fft', xla_client.FftType.FFT, a, n=n, axis=axis,
                        norm=norm)

# in /ivy/functional/frontends/jax/numpy/fft.py

import jax
from tensorflow.python.framework.test_ops import a

jax.numpy.fft.fft(a, n=None, axis=- 1, norm=None)
```

You can learn more about Ivy and UnifyAI at [https://unify.ai/]([url](https://unify.ai/)https://unify.ai/).
