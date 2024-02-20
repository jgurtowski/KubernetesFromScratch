# LibElektra
![Elektra Logo](images/elektralogo.svg)
Homepage: [https://www.libelektra.org](https://www.libelektra.org)

# Summary

Elektra attempts to build an abstraction over configuration files. It's focused on providing a better configuration management experience for Application developers, but has the ability to make system administrator's jobs easier by providing a way to work with existing configuration files.

Similar to AppConfig from AWS or other hosted configuration platforms but runs locally.

The fundamental idea is mapping a 'filesystem' like 'path' to a configuration variable.

for instance, within the Elektra framework the path /etc/portage/hello Could be mapped to value 'world'

```
kdb set /etc/portage/hello "world"
```

Elektra provides a library for applications to pick up this configuration.

For compatibility, Elektra has 'backends' that can map this abstract 'path' (/etc/portage/world) to a file in any format you desire (ini, json etc)

# Interesting idea, but not suitable for full system configuration management

1. Only handles configuration files. Processes, commands, file transfers must be done another way.
2. Certain packages have complicated configuration. They have created their own DSLs. Elektra can't hope to implement all of these.
3. Designed primarily for configuring a single system.

