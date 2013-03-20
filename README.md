NAME: gsl

VERSION: .011  

AUTHOR: Felix

AUTHOR_EMAIL: felix-language@googlegroups.com

MAINTAINER: mike.maul@gmail.com

PKG_URL: https://github.com/mmaul/gsl

DESCRIPTION: Gnu Scientific Library

CATEGORY: math

LIBDIR: gsl

-----
Gnu Scientific Library

## Requirements ##

You will need to have gsl, libcblas, libblas and lapack installed to use
this package

## Installation ##

* 'install' must be able to write to Felix INSTALL_ROOT

    scoop get gsl
    scoop build gsl

if building as root or installation directory is write-able by you

    scoop install gsl

Otherwise ( Installs what you just built as you not what root would rebuild )

     su # or sudo -s
     scoop install gsl --litterbox=/home/<your username>/.felix/litterbox

## Documentation ##

See gsl/*.flx
Also see tests in the source distribution. Not many but gsl is freakin
huge. The binding pretty much mirrors header files so just refer
to gsl doucmention and spin-it felix style.

## Example ##

This shoudl give you an idea of how to work with the rest of the library

    include "gsl/gsl_rng_lib";
    include "gsl/gsl_randist_lib";
    open gsl_rng_h;
    open gsl_randist_h;
    open C_hack;
    
    var r = gsl_rng_alloc(gsl_rng_mt19937);
    var n=10;
    println$ "     gauss      gamma    gumbel1";
    println$ "  ------------------------------";
    for var i in 0 upto n do
      var gauss = gsl_ran_gaussian(cptr(r),2.0);
      var gamma = gsl_ran_gamma(cptr(r),2.0,3.0);
      var gumbel1 = gsl_ran_gumbel1(cptr(r),2.0,3.0);
      println$ fmt_default(gauss,10,2) + "," + fmt_default(gamma,10,2)
      + "," + fmt_default(gumbel1,10,2);
    done

## Bugs/Problems ##

GSL is huge, and little of it has been tested in this binding. If you have 
problems send them to the list. If you find a bug and fix it or have an 
enhancement you can submit a pull request at github.

## License ##

THIS WRAPPER IS may be FFAU .. if it isn't it will be GPL.
but I'm waiting for the Gnu to get back to me on for a determination.
Code LINKED against will, however, may be governed
by the GPL licence, RTFL
