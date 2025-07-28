# Securing Interfaces

!!! note TODO
    - Present from a high level POV the problem of trust boundaries within software systems, using the well know examples e.g. command line arguments
    - Explain that when compartmentalizing we add more trust boundaries within software which means interfaces between compartment must be designed with that in mind
        - And, if retrofitting compartmentalization, the interfaces must be hardened (because they have not been designed as trust boundaries
    - From the COnffuzz paper list the problems that can happen when not securing interfaces, conclude that they negate most benefits of compartmentalization
    - Using the running example, show how the interfaces can be secured for that particular program. Ideally it would be a bit more complex than just adding a few checks.