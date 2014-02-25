# wirbelsturm-rpm-kafka

Builds an RPM based on an official [Apache Kafka](http://kafka.apache.org) binary release, using
[fpm](https://github.com/jordansissel/fpm).

Unfortunately the official Kafka project does not release ready-to-use RPM packages.  The RPM
script in this repository closes that gap.

---

Table of Contents

* <a href="#bootstrap">Bootstrapping</a>
* <a href="#supported-os">Supported target operating systems</a>
* <a href="#usage">Usage</a>
    * <a href="#build">Building the RPM</a>
    * <a href="#verify">Verifying the RPM</a>
    * <a href="#configuration">Custom configuration</a>
* <a href="#contributing">Contributing</a>
* <a href="#license">License</a>

---

<a name="bootstrap"></a>

# Bootstrapping

After a fresh checkout of this git repo you should first bootstrap the code.

    $ ./bootstrap

Basically, the bootstrapping will ensure that you have a suitable [fpm](https://github.com/jordansissel/fpm) setup.
If you already have `fpm` installed and configured you may try skipping the bootstrapping step.


<a name="supported-os"></a>

# Supported operating systems

## OS of the build server

It is recommended to run the RPM script [kafka-rpm-.sh](kafka-rpm.sh) on a RHEL OS family machine.


## Target operating systems

The RPM files are built for the following operating system and architecture:

* RHEL 6 OS family (e.g. RHEL 6, CentOS 6, Amazon Linux), 64 bit


<a name="usage"></a>

# Usage


<a name="build"></a>

## Building the RPM

Syntax:

    $ ./kafka-rpm.sh <kafka-package-download-url>

To find a direct download URL visit the [Kafka downloads](http://kafka.apache.org/downloads.html) page and click on the
link to a Kafka binary release.  Note: Don't use the (mirror) link on the download page because that link will first
take you to one of the Apache mirror sites.  Use one of the mirrors' direct links.

Example:

    $ ./kafka-rpm.sh http://www.eu.apache.org/dist/kafka/0.8.0/kafka_2.8.0-0.8.0.tar.gz

    >>> Will create kafka-0.8.0.el6.x86_64.rpm

This will create an RPM that contains all Kafka files and directories under the directory path `/opt/kafka/`.


<a name="verify"></a>

## Verify the RPM

You can verify the proper creation of the RPM file with:

    $ rpm -qpi kafka-*.rpm    # show package info
    $ rpm -qpR kafka-*.rpm    # show package dependencies
    $ rpm -qpl kafka-*.rpm    # show contents of package


<a name="configuration"></a>

## Custom configuration

You can modify [kafka-rpm.sh](kafka-rpm.sh) directly to modify the way the RPM is packaged.  For instance, you can
change the root level directory to something other than `/opt/kafka/`, or modify the name of the package maintainer.


<a name="contributing"></a>

## Contributing to wirbelsturm-rpm-kafka

Code contributions, bug reports, feature requests etc. are all welcome.

If you are new to GitHub please read [Contributing to a project](https://help.github.com/articles/fork-a-repo) for how
to send patches and pull requests to wirbelsturm-rpm-kafka.


<a name="license"></a>

## License

Copyright © 2014 Michael G. Noll

See [LICENSE](LICENSE) for licensing information.
