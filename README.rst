.. image:: https://img.shields.io/badge/sitcomtn--159-lsst.io-brightgreen.svg
   :target: https://sitcomtn-159.lsst.io
.. image:: https://github.com/lsst-sitcom/sitcomtn-159/workflows/CI/badge.svg
   :target: https://github.com/lsst-sitcom/sitcomtn-159/actions/

#########################################################################################################################################################
Determining the Accuracy and Precision of Astrometric Positions and Covariances from the LSST Science Pipelines Using Rubin's Operations Rehearsal 3 Data
#########################################################################################################################################################

SITCOMTN-159
============

We carry out an investigation into the veracity of the astrometric uncertainties calculated by the LSST pipeline.   
We use the Operations Rehearsal 3 dataset, and thus our results study the effect of the pipeline alone.  
Whilst there are regimes in which the pipeline astrometric uncertainties are a good estimate of the true uncertainty, there are also regimes in which they are underestimated, and one regime where they are overestimated.

Our analysis is based on creating distributions of separations between detections in the simulation's truth table and their counterparts in the pipeline's data tables for narrow windows of magnitude, pipeline-derived astrometric precision, and (where appropriate) on-sky source density.
From these distributions we can derive the actual uncertainties in these windows, and hence derive relationships between our measured uncertainties, and those provided by the pipeline.
For the Source table, single-visit detections we find there is a systematic uncertainty of 0.003-0.007 arcsec (3-7 mas) which has to be added in quadrature to the pipeline uncertainty, with a weak decreasing relationship with increasing field density.
This suggests that at fainter magnitudes (lower signal-to-noise ratios) the pipeline is correctly modelling all contributions to astrometric uncertainty, and that the deviations from "true" position are accurately reflected in the corresponding confidence in the measured position.
For the very brightest objects a small -- but significant relative to the statistical uncertainty -- source of astrometric noise is not being included in the pipeline uncertainties, perhaps from sources such as the global World Coordinate System solution, or missing sources of noise not being propagated through the full pipeline.
On the other hand, for Object table, coadded image detections, this simple model does not hold.
Instead we find a power-law relationship between pipeline-derived and measured astrometric precisions, with a power-law slope of approximately 0.75, the origin of which we are unable to explain easily.
Combining all simulated pointings, we find a very tentative sub-arcsecond (0.6 mas) plateau of best-achieved astrometric precision for Operations Rehearsal 3 Object tables.
We however caution that these results are relatively limited, due to the nature of the simulated fields chosen for the Operations Rehearsal, and that further investigations on "real" commissioning data -- including fields with a higher density of (stellar) objects -- will be necessary to determine the universality of these conclusions.

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
