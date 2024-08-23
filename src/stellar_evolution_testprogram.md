## Stellar evolution test program
Here, we describe a simple stand-alone program that uses the API to interface with a stellar evolution library.
We also use the units library (TODO: describe how this should work).

### In Pseudocode
```
use units(solar_mass, solar_radius, solar_luminosity, kelvin, year)

program main:
    initial_mass = solar_mass(input())

    result = initialise_code()
    star, result = new_star(initial_mass)
    result = evolve_step(star)
    age, result = get_age(star)
    mass, result = get_mass(star)
    radius, result = get_radius(star)
    luminosity, result = get_luminosity(star)
    temperature, result = get_luminosity(star)
    print(age, mass, radius, luminosity, temperature)
```
