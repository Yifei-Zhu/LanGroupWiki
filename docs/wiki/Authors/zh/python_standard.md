---
layout: page
title: 如何规范书写 Python 代码
author: Yifei Zhu
comments: true

---
## 前言
严格来讲，只要遵循正确的代码语法，代码语言是没有严格的规范的。
但为了代码的可读性，代码应遵循相应规范。
比如 Python 代码需要遵循 **PEP8代码规范**（[官方文档](https://peps.python.org/pep-0008/)/[中文版](https://link.zhihu.com/?target=https%3A//zh-google-styleguide.readthedocs.io/en/latest/google-python-styleguide/python_language_rules/%23id1)）。

为方便大家参考、调用、协作、统一管理，希望大家以统一的范式上传 Python 代码，本文将结合具体的例子示范：**在本课题组共同协作的背景下，该如何规范的书写 Python 代码。**
这里仅关注于一些需强调的以及常常出现问题的点，而具体细则将不再赘述。


## 示例：

```Python
class Calculator:
    """
    A simple calculator class for performing basic arithmetic operations.
    """

    def __init__(self):
        """
        Initializes the Calculator.
        """
        pass

    def add(self, a: float, b: float) -> float:
        """
        Adds two numbers.

        :param a: First number, a float.
        :param b: Second number, a float.
        :return: Sum of a and b, a float.
        """
        return a + b

    def subtract(self, a: float, b: float) -> float:
        """
        Subtracts two numbers.

        :param a: First number, a float.
        :param b: Second number, a float.
        :return: Difference between a and b, a float.
        """
        return a - b

        
    """Predict using the kernel ridge model.

    Parameters
    ----------
    X : {array-like, sparse matrix} of shape (n_samples, n_features)
        Samples. If kernel == "precomputed" this is instead a
        precomputed kernel matrix, shape = [n_samples,
        n_samples_fitted], where n_samples_fitted is the number of
        samples used in the fitting for this estimator.

    Returns
    -------
    C : ndarray of shape (n_samples,) or (n_samples, n_targets)
        Returns predicted values.
    """
```

## 其他
