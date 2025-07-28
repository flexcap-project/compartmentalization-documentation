# What is Compartmentalization?

Software compartmentaliaation is a software engineering practice where developers break down a program into groups of isolated and distrusting components, called compartments, each controlling only the resources they require to do their tasks. Software compartmentalization is an embodiment of the principle of least privilege: by ensuring that each part of the program only runs with the least set of privileges necessary to complete its job, we can reduce the damage caused by a bug or compromise. Think of a compartment like a box containing part of a program. If a software component is compromised in a compartmentalized program, for example through a zero-day bug, attackers will be restricted to the permissions and capabilities of the compromised component. To escalate privileges and compromise the rest of the system, attackers will need to find a way to escape from the compartment.

!!! note "TODO here"
    - Maybe remind explain that the concept of compartmentalization comes from (and provides analogous protection) various safety fields, e.g. [ship design](https://en.wikipedia.org/wiki/Compartment_%28ship%29), [fire protection](https://en.wikipedia.org/wiki/Fire_compartmentation).
    - Give the usual example: a web server with a bit that is not fully trusted (e.g. http parser) and another bit that is security critical (e.g. crypto library): a typical attack leverages a vulnerability in the parser to access the crypto library. Explain how compartmentalization cna help.

## Why would I compartmentalize?

!!! note "TODO here"
    - What we need here is a motivation about compartmentalization, not a list of trust models (that should come later)
    - Summarize all the benefits (maybe link to the next chapter), insist on supply chain attacks and other vulnerabilities that are unknown or that do not even exist yet
    - Software is getting more an more complex, these issues are becoming more concerning

## Properties Enforced

!!! note "TODO"
    - CIA triad

## Trust Models

Broadly there are three main trust models:

1. **Sandboxing**: here part of a program is *sandboxed*, meaning that the rest of the system is protected from it. This means that the sandbox is untrusted and whatever resides within the sandbox is contained and prevented from causing damage. We may choose to sandbox untrusted components, third-party components, code handling untrusted input or anything which may be buggy.

2. **Safeboxing**: here a part of a program is *protected* from the rest of the system. This is typically applied to sensitive data or components eg. crypto keys to protect them from malicious interference. In this trust model everything in a safebox is trusted. A safebox can access the untrusted portion of the system but the untrusted portion cannot access the safebox.

3. **Mutual Distrust**: in this trust model, compartments distrust each other and compartmentalization is implemnted in such a way that compartments are protected from other compartments.

## What Software Can/Should be Compartmentalized?

Compartmentalization can be applied to any piece of software, including but not limited to: applications, kernels, operating systems, hypervisors, firmware and language runtimes. 

!!! "TODO here"
    - Give concrete example of existing compartmentalized software running in production
    - Software that benefit from compartmentalization: when you cannot see your app anymore as a single unit of trust (most software would fit that descirption these days as they e.g. integrate source code coming from various sources of variable trustworthiness)
    - Ack that it's not widespread, point out the regain of popularity due to recent technology (isolation mechanisms, compilers techniques) improvements + growing cyber security concerns
    - Present designing for compartmentalization vs. retrofitting it