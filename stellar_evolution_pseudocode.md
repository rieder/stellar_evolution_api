# Stellar Evolution API v0.1
This document describes function signatures for a stellar evolution API in pseudo code.

The API is based on the API used in [AMUSE](https://amuse.readthedocs.io/en/latest/reference/introduction_interface_specification.html) and is further inspired by [FDPS](https://github.com/FDPS/FDPS/blob/master/doc/doc_specs_cpp_en.pdf).

See also: [https://github.com/amusecode/amuse/blob/main/src/amuse/community/interface/se.py]

## Initialise

```
function initialise_code:
    in:
    out: result

    # initialises the code 
    result =
       0  if succesful
       -1 if not implemented
       another number if an error occurred
```

## Add a star

```
function new_particle:
    in: mass
    out: result, star_index

    # creates a new star, with mass 'mass'
    # star_index is a unique identifier for this star, should not be re-used if the star is deleted
    result =
       0  if succesful
       -1 if not implemented
       another number if an error occurred
```

## Evolve a star

```
function evolve_one_step:
    in: star_index
    out: result

    # evolves star(star_index) for one time step
    result =
       0  if successful
       -1 if not implemented
       another number if an error occurred
```

```
function evolve_for:
    in: star_index, time_delta
    out: result

    # evolves star(star_index) for exactly the given time
    result =
       0  if successful
       -1 if not implemented
       another number if an error occurred
```

## Retrieve value

```
function get_stellar_type:
    in: star_index
    out: result, stellar_type

    # sets stellar_type to the evolution stage of the star (MS, WD, RGB, etc)
    stellar_type = star(star_index).stellar_type
    result = 
       0  if successful
       -1 if not implemented
       another number if an error occurred   
```
```
function get_mass:
    in: star_index
    out: result, mass

    # sets mass to be the current mass of star(index)
    mass = star(star_index).mass
    result = 
       0  if successful
       -1 if not implemented
       another number if an error occurred
```
```
function get_age:
    in: star_index
    out: result, age

    # sets age to be the current age of star(index)
    age = star(star_index).age
    result = 
       0  if successful
       -1 if not implemented
       another number if an error occurred
```
(analoguous: radius, temperature, luminosity, time step)
```
function get_star_property_by_name:
    in: star_index, property_name
    out: result

    # sets value to be the current value of star(index).[property_name]
    value = star(star_index).[property_name]
    result = 
       0  if successful
       -1 if not implemented
       another number if an error occurred
```
```
function get_global_property_by_name:
    in: property_name
    out: result

    # sets value to be the current value of global property [property_name]
    value = [property_name]
    result = 
       0  if successful
       -1 if not implemented
       another number if an error occurred
```
## Set value

```
function set_mass:
    in: star_index, mass
    out: result

    # sets mass of star(star_index) to mass
    star(star_index).mass = mass
    result = 
       0  if successful
       -1 if not implemented
       another number if an error occurred
```
```
function set_property_by_name:
    in: star_index, property_name, value
    out: result

    # sets star(index).[property_name] to value
    star(star_index).[property_name] = value
    result = 
       0  if successful
       -1 if not implemented
       another number if an error occurred
```
