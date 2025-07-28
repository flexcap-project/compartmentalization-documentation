# What is Compartmentalization?

Software compartmentaliaation is a software engineering practice where developers break down a program into groups of isolated and distrusting components, called compartments, each controlling only the resources they require to do their tasks. Software compartmentalization is an embodiment of the principle of least privilege: by ensuring that each part of the program only runs with the least set of privileges necessary to complete its job, we can reduce the damage caused by a bug or compromise. Think of a compartment like a box containing part of a program. If a software component is compromised in a compartmentalized program, for example through a zero-day bug, attackers will be restricted to the permissions and capabilities of the compromised component. To escalate privileges and compromise the rest of the system, attackers will need to find a way to escape from the compartment.

## What would I compartmentlize?

Compartmentalization can be applied to any piece of software, including but not limited to: applications, kernels, operating systems, hypervisors, firmware and language runtimes. Broadly there are three main trust models:
1. **Sandboxing**: here part of a program is *sandboxed*, meaning that the rest of the system is protected from it. This means that the sandbox is untrusted and whatever resides within the sandbox is contained and prevented from causing damage. We may choose to sandbox untrusted components, third-party components, code handling untrusted input or anything which may be buggy.

2. **Safeboxing**: here a part of a program is *protected* from the rest of the system. This is typically applied to sensitive data or components eg. crypto keys to protect them from malicious interference. In this trust model everything in a safebox is trusted. A safebox can access the untrusted portion of the system but the untrusted portion cannot access the safebox.

3. **Mutual Distrust**: in this trust model, compartments distrust each other and compartmentalization is implemnted in such a way that compartments are protected from other compartments.

## Example
