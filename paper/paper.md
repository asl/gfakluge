---
title: 'GFAKluge: A C++ library and command line utilities for the Graphical Fragment Assembly formats.'
tags:
  - GFA
  - C++
  - genome assembly
  - bioinformatics
authors:
 - name: Eric T. Dawson
   orcid:  0000-0001-5448-1653
   affiliation: "1, 2"
 - name: Richard Durbin
   orcid: 0000-0000-0000-0000
   affiliation: "2, 3"
affiliations:
 - name: Division of Cancer Epidemiology and Genetics, National Cancer Institute, Rockville, MD, USA
   index: 1
 - name: Department of Genetics, University of Cambridge, Cambridge, UK
   index: 2
 - name: Wellcome Trust Sanger Institute, Hinxton, UK
 - index: 3
date: 19 March 2018
bibliography: paper.bib
---

# Summary
GFAKluge is a set of command line utilities and a C++ library for parsing and
manipulating the Graphical Fragment Assembly format. 
Genome assembly algorithms often uses graph structures
to represent relationships between reads during the assembly process. Such information
is typically thrown away when assemblies are converted to FASTA; previous attempts to integrate 
graph information did not gain widespread acceptance largely because
they were difficult for humans to parse. The Graphical Fragment Assembly
(GFA) format was proposed as a way to encode the graph structure of an assembly in a human-readable
text format. 
GFA also aims to provide a single format for interchange between software for assembly,
visualization, read mapping and variant calling. Such programs are often written in high-performance
programming languages such as C or C++. GFAKluge facilitates interprogram exchange by providing
a high-level API in C++ under the MIT software license. We hope the availability of an open-source,
easily extensible API will encourage software developers to consider adding support for GFA to their
bioinformatics programs.

GFAKluge also provides a command line interface for working with GFA. This includes replacements for
common tasks on FASTA assemblies such as calculating assembly N90. There are also methods for merging
assemblies, reformating files for readability, and converting between legacy GFA formats.

# Integrating GFAKluge into an existing program
As an example of how to use the GFAKluge API, we examine its use in the variation graph toolkit [vg](https://github.com/vgteam/vg).
vg creates string graphs from assemblies and population variation that are then used for read mapping and variant calling. We incorporated
GFAKluge for input and output of GFA in vg, replacing an existing parser. Reading in a GFA file requires one line of code and is agnostic to
the GFA version used. Converting from GFA to vg's internal structures and vice versa requires forty source lines of code. Changing output from
GFA v1.0 to GFA v2.0 requires a single API call. This allows vg to take assemblies in GFA format from TwoPaCo and other assembly algorithms.
The gfak command line tools can be used to calculate assembly statistics on assemblies produced by vg.