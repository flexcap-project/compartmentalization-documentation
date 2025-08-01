# Why Compartmentalization?

Compartmentalization is an invaluable technique for software developers.
It is useful for the following reasons:

!!! note TODO
    - Consider putting the second point first?

1. **Compartmentalizing to contain memory-safety issues.**
   Containing memory safety issues is a popular use-case of software compartmentalization: software parts which are more likely to feature memory-safety bugs (e.g., performing error-prone tasks such as parsers), or components where bugs are most likely to be exploited (e.g those facing the network) are isolated into an unprivileged compartment (sandbox) to limit the impact of future, unknown bugs.
   By virtue of memory isolation, memory safety issues affecting these components are then contained within their originating compartment.

2. **Compartmentalizing to protect against untrusted dependencies.**
   Another application of software compartmentalization is protecting a program against untrusted dependencies.
   Such cases take place when either the supply chain or the dependency itself are distrusted or considered compromised.
   In a monolithic program, the impact of relying on an untrusted dependency corresponds to granting attackers with permissions to execute arbitrary code, regardless of whether or not the dependency is written in a safe language.
   Here too, sandboxing can help mitigate the impact of a malicious or compromised dependency.

3. **Compartmentalizing to protect critical data and code.** Programs often embed data which demands special protection.
   Such data includes program secrets (e.g., cryptographic keys, passwords and credentials, more broadly authentication data), as well as data critical to enforcing security mechanisms (e.g., shadow stacks, CPI and CPS regions, randomisation information, or page tables in the kernel).
   Similarly, programs often embed code sections which require elevated privileges, for instance performing a system call such as setuid or setgid to change user IDs, known to cause serious vulnerabilities when subverted.
   In all cases, compartmentalization can be employed to prevent illegitimate accesses to critical data or code.
   This type of compartmentalization differs from 1 and 2 in that it is not directed at the part of the program which is distrusted, but at the one which is trusted.
   We refer to this model as safebox, by opposition to the sandbox model (1-2).
   An example of this use-case is isolating OpenSSL to protect cryptographic keys.

4. **Compartmentalizing to make software more reliable.**
   If one component of a monolithic program crashes, becomes unresponsive, or misbehaves, so does the entire program.
   Software compartmentalization increase program reliability: by introducing boundaries between components, individual program parts can be restarted without impacting the whole, provided program state is appropriately segregated.
