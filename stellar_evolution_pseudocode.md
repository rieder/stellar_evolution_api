# Stellar Evolution API v0.1
This document describes function signatures for a stellar evolution API in pseudo code

## Evolve a star

```
function evolve_star(star_index, time_end, result):
    in: star_index, time_end
    out: result

    # evolves star(star_index) until it either
    # - reaches time_end exactly, or
    # - reaches the first time step after this
    result =
       0  if successful
       -1 if not implemented
       another number if an error occurred
```

## Retrieve value

```
function get_mass(star_index, mass, result):
    in: star_index
    out: result, mass

    # sets mass to be the current mass of star(index)
    mass = star(star_index).mass
    result = 
       0  if successful
       -1 if not implemented
       another number if an error occurred
```

## Set value

```
function set_mass(star_index, mass, result):
    in: star_index, mass
    out: result

    # sets mass of star(star_index) to mass
    star(star_index).mass = mass
    result = 
       0  if successful
       -1 if not implemented
       another number if an error occurred
```
