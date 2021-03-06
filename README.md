# `ppmlhdfe`: Poisson pseudo-likelihood regression with multiple levels of fixed effects

- Current version: ` 2.0.1 03mar2019`
- Jump to: [`citation`](#citation) [`references`](#references) [`install`](#installation)
- Also see: [`ppmlhdfe` Paper](http://scorreia.com/research/ppmlhdfe.pdf) | [Separation Paper](http://scorreia.com/research/separation.pdf) | [Help File](http://scorreia.com/help/ppmlhdfe.html) | [Separation Primer](https://github.com/sergiocorreia/ppmlhdfe/blob/master/guides/separation_primer.md) | [Separation Benchmarks](https://github.com/sergiocorreia/ppmlhdfe/blob/master/guides/separation_benchmarks.md) | [Undocumented](https://github.com/sergiocorreia/ppmlhdfe/blob/master/guides/undocumented.md)


**ppmlhdfe** is a Stata package that implements Poisson pseudo-maximum likelihood regressions (PPML) with multi-way fixed effects, as described in [Correia, Guimarães, Zylkin (2019a)](http://scorreia.com/research/ppmlhdfe.pdf). The estimator employed is robust to statistical separation and convergence issues, due to the procedures developed in [Correia, Guimarães, Zylkin (2019b)](http://scorreia.com/research/separation.pdf).


## Citation

#### Text

<ul>
<li>
Sergio Correia, Paulo Guimarães, Thomas Zylkin: “Verifying the existence of maximum likelihood estimates for generalized linear models”, 2019; <a href='http://arxiv.org/abs/1903.01633'>arXiv:1903.01633</a>.
</li>
</ul>

<ul>
<li>
Sergio Correia, Paulo Guimarães, Thomas Zylkin: “ppmlhdfe: Fast Poisson Estimation with High-Dimensional Fixed Effects”, 2019; <a href='http://arxiv.org/abs/1903.01690'>arXiv:1903.01690</a>.
</li>
</ul>

#### Bibtex

```bibtex
@Misc{1903.01633,
  Author = {Sergio Correia and Guimar{\~a}es and Thomas Zylkin},
  Title = {Verifying the existence of maximum likelihood estimates for generalized linear models},
  Year = {2019},
  Eprint = {arXiv:1903.01633},
}

@Misc{1903.01690,
  Author = {Sergio Correia and Guimar{\~a}es and Thomas Zylkin},
  Title = {{ppmlhdfe: Fast Poisson Estimation with High-Dimensional Fixed Effects}},
  Year = {2019},
  Eprint = {arXiv:1903.01690},
}
```


## References

Quick information on the command can be glanced from the [help file](http://scorreia.com/help/ppmlhdfe.html).

For detailed information:

- The [ppmlhdfe paper](http://scorreia.com/research/ppmlhdfe.pdf) explains the command in depth, provides examples, etc.
- The paper on [statistical separation](http://scorreia.com/research/separation.pdf) discusses the crucial step of solving the separation issue, that can otherwise lead to incorrect convergence (or no convergence) in Poisson and other GLM models.

For introductory guides on separation, and on how `ppmlhdfe` internally address it, see the following documents:

- [Separation primer](https://github.com/sergiocorreia/ppmlhdfe/blob/master/guides/separation_primer.md): a quick practical introduction to separation in Poisson models.
- [Separation benchmarks](https://github.com/sergiocorreia/ppmlhdfe/blob/master/guides/separation_benchmarks.md): shows how separation affects all common statistical packages.
- [Undocumented options](https://github.com/sergiocorreia/ppmlhdfe/blob/master/guides/undocumented.md): this pages briefly lists otherwise undocumented options of `ppmlhdfe`, which might be useful for advanced users.


## Installation

`ppmlhdfe` requires the latest versions of [`ftools`](https://github.com/sergiocorreia/ftools) and [`reghdfe`](https://github.com/sergiocorreia/reghdfe).

To install stable versions from SSC:

```stata
cap ado uninstall ftools
cap ado uninstall reghdfe
cap ado uninstall ppmlhdfe

ssc install ftools
ssc install reghdfe
ssc install ppmlhdfe

clear all
ftools, compile
reghdfe, compile

* Test program
sysuse auto, clear
reghdfe price weight, a(turn)
ppmlhdfe price weight, a(turn)
```

To install the latest versions from Github:

```stata
* Install ftools
cap ado uninstall ftools
net install ftools, from("https://raw.githubusercontent.com/sergiocorreia/ftools/master/src/")

* Install reghdfe
cap ado uninstall reghdfe
net install reghdfe, from("https://raw.githubusercontent.com/sergiocorreia/reghdfe/master/src/")

* Install ppmlhdfe
cap ado uninstall ppmlhdfe
net install ppmlhdfe, from("https://raw.githubusercontent.com/sergiocorreia/ppmlhdfe/master/src/")

* Create compiled files
ftools, compile
reghdfe, compile

* Check versions
ppmlhdfe, version

* Clear programs already in memory
program drop _all

* Test program
sysuse auto, clear
reghdfe price weight, a(turn)
ppmlhdfe price weight, a(turn)
```
