# Defining a Policy


## What is a compartmentalization policy?
Compartmentalization policy describes the compartmentalization policies and properties which should be enforced. This directly impacts the requirements and impacts of compartmentalization such as the performance impact.

Policy definition can be broken down into two tasks:

1) Deciding which parts of a program to compartmentalize,
2) Deciding which permissions to enforce on each compartment.

### Which parts of a program
To begin, it is useful to consider the goals you wish to achieve through compartmentalization. Do you wish to isolate pontentially buggy software components or protect against third party dependencies? Sandboxing those dependencies may be the way to go. Protecting sensitive data? Safeboxing those components may be sensible.

#### Code or data centric?

### Permissions
