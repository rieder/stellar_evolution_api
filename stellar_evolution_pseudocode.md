# Stellar Evolution API v0.1
This document describes function signatures for a stellar evolution API in pseudo code.

The API is directly based on the API used in [AMUSE](https://amuse.readthedocs.io/en/latest/reference/introduction_interface_specification.html).

See also: [https://github.com/amusecode/amuse/blob/main/src/amuse/community/interface/se.py]

## Basic code functions

```
function initialise_code:
    in:
    out: result

    # initialises the code 
    result =
        0 - OK
            Code is initialized
        -1 - ERROR
            Error happened during initialization, this error needs to be
            further specified by every code implemention
        -2 - ERROR
            not yet implemented
```

## Add a star

```
function new_star:
    in: mass
    out: result, star_index

    # creates a new star, with mass 'mass'
    # star_index is a unique identifier for this star, should not be re-used if the star is deleted
    result =
        0 - OK
            New star was loaded and the star_index parameter set.
        -1 - ERROR
            New star could not be created.
```

## Delete a star

```
function delete_star:
    in: star_index
    out: result

    # deletes a star
    result =
        0 - OK
            The star has been deleted
        -1 - ERROR
            A star with the given index was not found.
```

## Evolve a star

```
function evolve_one_step:
    in: star_index
    out: result

    # evolves star(star_index) for one time step
    result =
        0 - OK
            The star was evolved.
        -1 - ERROR
            The evolution could not complete, solution did not converge.
```

```
function evolve_for:
    in: star_index, time_delta
    out: result

    # evolves star(star_index) for exactly the given time
    result =
        0 - OK
            The star was evolved.
        -1 - ERROR
            The evolution could not complete, solution did not converge.
```

## Retrieve value

```
function get_stellar_type:
    in: star_index
    out: result, stellar_type

    # sets stellar_type to the evolution stage of the star (MS, WD, RGB, etc)
    stellar_type = star(star_index).stellar_type
    result = 
        0 - OK
            The value has been set.
        -1 - ERROR
            A star with the given index was not found.
```
```
function get_mass:
    in: star_index
    out: result, mass

    # sets mass to be the current mass of star(index)
    mass = star(star_index).mass
    result = 
        0 - OK
            The value has been set.
        -1 - ERROR
            A star with the given index was not found.
```
```
function get_age:
    in: star_index
    out: result, age

    # sets age to be the current age of star(index)
    age = star(star_index).age
    result = 
        0 - OK
            The value has been set.
        -1 - ERROR
            A star with the given index was not found.
```
(analoguous: radius, temperature, luminosity, time step)
```
function get_star_property_by_name:
    in: star_index, property_name
    out: result

    # sets value to be the current value of star(index).[property_name]
    value = star(star_index).[property_name]
    result = 
        0 - OK
            The value has been set.
        -1 - ERROR
            A star with the given index was not found.
        -2 - ERROR
            The given property was not found for the star.
```
```
function get_global_property_by_name:
    in: property_name
    out: result

    # sets value to be the current value of global property [property_name]
    value = [property_name]
    result = 
        0 - OK
            Current value of the given property was retrieved.
        -1 - ERROR
            The code does not have support for retrieving the given property.
```
## Set value

```
function set_global_property_by_name:
    in: star_index, property_name, value
    out: result

    # sets star(index).[property_name] to value
    star(star_index).[property_name] = value
    result = 
        0 - OK
            Current value of the given property was set.
        -1 - ERROR
            The code does not have support for updating the given property.
```
