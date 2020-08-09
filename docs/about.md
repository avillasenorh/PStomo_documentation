# About PStomo

PStomo is a seismic tomography program written in C that inverts first-arriving P (and S) wave
arrival times to obtain a P (and S) wave velocity model. PStomo can use any combination
of controlled sources (e.g. explosions) and natural sources (earthquakes). When using earthquakes,
PStomo can jointly invert both for velocity structure and earthquake relocation.

## Authors

The current version of PStomo has been developed by Ari Tryggvason,
Department of Earth Sciences, Uppsala University, Uppsala, Sweden.

The original program was created by Harley M. Benz at the U.S. Geological Survey.
The finite difference algorithms were written by John Vidale, John Hole,
Pascal Podvin and Isabel Lecomte (see the reference list).
The (modified) LSQR algorithm was created by Paige and Saunders (1982).
The (slightly modified) SVD algorithms are taken from Numerical Recipes in C (Press et al., 1988).

Yao Zheng Shen created the algorithms for generating the output for computing the
resolution matrix with LSQR (Yao, et al., 1999).

Antonio Villaseñor created initial versions of some of the GMT scripts used in the tutorial examples.

## License

Choose a license such as MIT.

## References

Benz, H. M., B.A. Chouet, P. B. Dawson, J. C. Lahr, R. A. Page, and J. A. Hole (1996). Three- dimensional P- and S-wave velocity structure of Redoubt Volcano, Alaska, J. geophys. Res., 101, 8111-8128.

Hole, J. A. (1992). Nonlinear high-resolution three-dimensional seismic travel time tomography, J. geophys. Res., 97, 6553-6562.

Hole, J. A., and B. C. Zelt (1995). 3-D finite-difference reflection traveltimes. Geophys. J. Int., 121, 427-434.

Paige, C. C., and M. A. Saunders (1982). LSQR: An algorithm for sparse linear equations and sparse least squares. ACM Trans. Math. Software, 8, 43-71.

Podvin, P., and I. Lecomte (1991). Finite difference computation of traveltimes in very contrasted velocity models. A massively parallel approach and its associated tools, Geophys. J. Int, 105, 271-284

Press, W. H., S. A. Teukolsky, W. T. Vetterling, and B. P. Flannery (1988). Numerical recipes in C, Cambridge University Press.

Tryggvason, A., and N. Linde (2006). Local earthquake (LE) tomography with joint inversion for P- and S-wave velocities using structural constraints. Geophys. Res. Lett., 33, L07303, doi:10.1029/2005GL025485.

Wessel. P., and W. H. F. Smith (1998). New improved version of Generic Mapping Tools released. EOS Trans. Amer. Geophys. U., 79(47), 579.

Yao, Z. S., R. G. Roberts, and A. Tryggvason (1999). Calculating resolution and covariance matrixes for seismic tomography with the LSQR method. Geophys. J. Int, 138, 886-894, doi:10.1046/j.1365-246x.1999.00925.x.
