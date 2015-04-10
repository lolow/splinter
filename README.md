##Splinter
Splinter (SPLine INTERpolation) is a function approximation library implementing various multivariate splines in C++. With Splinter you can approximate any function in any number of variables using the following implementations:

1. a speedy implementation of the tensor product [B-spline](http://en.wikipedia.org/wiki/B-spline), and 
2. a simple implementation of [radial basis function splines](http://en.wikipedia.org/wiki/Radial_basis_function), including the [thin plate spline](http://en.wikipedia.org/wiki/Thin_plate_spline).

The B-spline may approximate any multivariate function sampled on a grid. The user may construct a linear (degree 1), quadratic (degree 2) or cubic (degree 3) spline that interpolates the data. The B-spline is constructed from the samples by solving a linear system. On a modern desktop computer the practical limit on the number of samples is about 100 000 when constructing a B-spline. However, evaluation time is independent of the number of samples due to the local support property of B-splines. That is, only samples neighbouring the evaluation point affect the B-spline value. Evaluation do however scale with the degree and number of variables of the B-spline.

The user may create a penalized B-spline (P-spline) that smooths the data instead of interpolating it. The construction of a P-spline is more computationally demanding than the B-spline - a large least-square problem must be solved - bringing the practical limit on the number of samples down to about 10 000.

When sampling is expensive and/or scattered (not on a grid) the radial basis function splines may be utilized for function approximation. The user should expect a high computational cost for constructing and evaluating a radial basis function spline, even with a modest number of samples (up to about 1 000 samples). 

The library is based on the C++ template linear algebra library [Eigen](http://eigen.tuxfamily.org); its sparse matrix support is particularly important for the speed of the tensor product B-spline implementation.

![Illustration of a B-spline](assets/bspline.png)
Figure: Illustration of a cubic B-spline generated with the Splinter library.

###Author's note
Splinter is the result of two years of work and development towards a fast and general spline library for function approximation. The initial intention with the library was to build splines for use in mathematical programming (nonlinear optimization). Thus, some effort has been put into functionality that supports this, e.g. Jacobian and Hessian computations for the B-spline. The current goals with the library are: 1) to make it more general than it is today, and 2) to implement and test new features that may be useful for anyone using the library (be it for computer-aided design or other graphical work, function approximation, mathematical programming, compression of data, etc.).

By making Splinter publicly available the author hopes to help anyone looking for a multivariate spline library, or just a library for multivariate interpolation (there aren't many publicly available multivariate interpolation libraries that support any number of variables). In return the author expects nothing but your suggestions, improvements, and feature requests. As the TODO-list reflects there are still much honing to be done!

Please let me know by e-mail what you think about the library. Questions related to installation should be directed to Anders Wenhaug (awenhaug@gmail.com). Together we will do our best to support your use of the library.

Best regards,

Bjarne Grimstad  (bjarne.grimstad@gmail.com)

###Requirements for use
* [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page) (tested with versions 3.2.1, 3.2.2 and 3.2.3)

###Guides
* [Installation](docs/install.md)
* [Basic usage](docs/basic_usage.md)
