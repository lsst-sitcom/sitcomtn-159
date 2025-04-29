.. image:: https://img.shields.io/badge/sitcomtn--159-lsst.io-brightgreen.svg
   :target: https://sitcomtn-159.lsst.io
.. image:: https://github.com/lsst-sitcom/sitcomtn-159/workflows/CI/badge.svg
   :target: https://github.com/lsst-sitcom/sitcomtn-159/actions/

##############################################################################################################################
Investigations into the Accuracy and Precision of Astrometric Positions and Covariances of Rubin's Operations Rehearsal 3 Data
##############################################################################################################################

SITCOMTN-159
============

In this work we carry out an initial investigation into the LSST Pipelines astrometric accuracy and precision.
For each of the available simulated tracts in Operations Rehearsal 3, we create distributions of nearest-neighbour match on-sky separations for narrow windows of magnitude, pipeline-derived astrometric precision, and (where appropriate) on-sky source density.
For a series of such cross-matches -- looping through a range of magnitudes and hence signal-to-noise ratios -- for the \texttt{Source} table, single-visit detections, we derive best-fit parameters such that we can correct the astrometric uncertainties to best match the separation distributions.
Fitting for both a systematic uncertainty $n$, to be added in quadrature to the pipeline uncertainty, and a multiplicative scaling factor for the quoted precisions $m$, we find, globally, that scaling factors are reasonable (and hence $m \approx 1\pm0.1$), while a systematic astrometric uncertainty of $n$ in the range 0.003-0.007 arcsec (3-7 mas) is necessary, with a weak decreasing relationship with increasing field density.
This suggests that at fainter magnitudes (lower signal-to-noise ratios) the pipeline is correctly modelling all contributions to astrometric uncertainty, and that the deviations from ``true'' position are accurately reflected in the corresponding confidence in the measured position.
On the other hand, for the very brightest objects a small -- but significant relative to the statistical uncertainty -- astrometric precision is not being recovered, from sources such as the global World Coordinate System solution, missing sources of noise not being propagated through the full pipeline, and so on.
For \texttt{Object} table, coadded image detections, this simple scaling relation does not hold.
Instead we find a power-law fit between pipeline-derived and best-fit astrometric precisions, with a power-law slope of approximately 0.75, the origin of which we are unable to explain easily.
Combining all simulated pointings we find a very tentative sub-arcsecond (0.6 mas) systematic plateauing astrometric precision for the Operations Rehearsal \texttt{Object} tables.
We however caution that these results are relatively limited, due to the nature of the simulated fields chosen as part of the Operations Rehearsal, and that further investigations on ``real'' commissioning data -- including fields with a higher density of (stellar) objects -- will be necessary to determine the universality of these conclusions.

Links
=====

- Live drafts: https://sitcomtn-159.lsst.io
- GitHub: https://github.com/lsst-sitcom/sitcomtn-159

Build
=====

This repository includes lsst-texmf_ as a Git submodule.
Clone this repository::

    git clone --recurse-submodules https://github.com/lsst-sitcom/sitcomtn-159

Compile the PDF::

    make

Clean built files::

    make clean

Updating acronyms
-----------------

A table of the technote's acronyms and their definitions are maintained in the ``acronyms.tex`` file, which is committed as part of this repository.
To update the acronyms table in ``acronyms.tex``::

    make acronyms.tex

*Note: this command requires that this repository was cloned as a submodule.*

The acronyms discovery code scans the LaTeX source for probable acronyms.
You can ensure that certain strings aren't treated as acronyms by adding them to the `skipacronyms.txt <./skipacronyms.txt>`_ file.

The lsst-texmf_ repository centrally maintains definitions for LSST acronyms.
You can also add new acronym definitions, or override the definitions of acronyms, by editing the `myacronyms.txt <./myacronyms.txt>`_ file.

Updating lsst-texmf
-------------------

`lsst-texmf`_ includes BibTeX files, the ``lsstdoc`` class file, and acronym definitions, among other essential tooling for LSST's LaTeX documentation projects.
To update to a newer version of `lsst-texmf`_, you can update the submodule in this repository::

   git submodule update --init --recursive

Commit, then push, the updated submodule.

.. _lsst-texmf: https://github.com/lsst/lsst-texmf
