# Introduction

Many codes exist for doing astrophysical simulations.
One of the domains where simulations are used is stellar evolution.
These codes can roughly be distinguished between stellar population codes, which rapidly model the evolution of one or multiple stars through the use of pre-calculated models/tracks/..., and Henyey style codes which model the interior of a star.
Often, stellar population codes are used in tandem with stellar dynamics codes (e.g. in AMUSE, MOCCA, PeTar).
To ensure that various stellar evolution codes can be used interchangeably for this purpose, we define a common application programming interface (API) for stellar evolution codes used in astrophysical simulations.

This API defines the signature used for external/public functions of the stellar evolution code.
We define this API for both a "mandatory" subset, which must be implemented in every code, and an "optional" subset, which codes may choose to support or not.
Additionally, we define a unit system which will ensure that conversions between units are valid, and that they use the same definitions (which is not currently always the case).
To check compatibility with the API defined here, we also provide a test suite.

We provide examples of this API being used in the codes SSE (REF), SeBa (REF) and GENEC (REF).
