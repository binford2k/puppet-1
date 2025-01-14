---
layout: default
built_from_commit: 812d7420ea5d7e19e8003b26486a7c8847afdb25
title: 'Man Page: puppet resource'
canonical: "/puppet/latest/man/resource.html"
---

# Man Page: puppet resource

> **NOTE:** This page was generated from the Puppet source code on 2024-10-18 17:22:50 +0000

## NAME
**puppet-resource** - The resource abstraction layer shell

## SYNOPSIS
Uses the Puppet RAL to directly interact with the system.

## USAGE
puppet resource \[-h\|\--help\] \[-d\|\--debug\] \[-v\|\--verbose\]
\[-e\|\--edit\] \[-p\|\--param *parameter*\] \[-t\|\--types\]
\[-y\|\--to_yaml\] *type* \[*name*\] \[*attribute*=*value* \...\]

## DESCRIPTION
This command provides simple facilities for converting current system
state into Puppet code, along with some ability to modify the current
state using Puppet\'s RAL.

By default, you must at least provide a type to list, in which case
puppet resource will tell you everything it knows about all resources of
that type. You can optionally specify an instance name, and puppet
resource will only describe that single instance.

If given a type, a name, and a series of *attribute*=*value* pairs,
puppet resource will modify the state of the specified resource.
Alternately, if given a type, a name, and the \'\--edit\' flag, puppet
resource will write its output to a file, open that file in an editor,
and then apply the saved file as a Puppet transaction.

## OPTIONS
Note that any setting that\'s valid in the configuration file is also a
valid long argument. For example, \'ssldir\' is a valid setting, so you
can specify \'\--ssldir *directory*\' as an argument.

See the configuration file documentation at
https://puppet.com/docs/puppet/latest/configuration.html for the full
list of acceptable parameters. A commented list of all configuration
options can also be generated by running puppet with \'\--genconfig\'.

\--debug

:   Enable full debugging.

\--edit

:   Write the results of the query to a file, open the file in an
    editor, and read the file back in as an executable Puppet manifest.

\--help

:   Print this help message.

\--param

:   Add more parameters to be outputted from queries.

\--types

:   List all available types.

\--verbose

:   Print extra information.

\--to_yaml

:   Output found resources in yaml format, suitable to use with Hiera
    and create_resources.

\--fail

:   Fails and returns an exit code of 1 if the resource could not be
    modified.

## EXAMPLE
This example uses **puppet resource** to return a Puppet configuration
for the user **luke**:



    $ puppet resource user luke
    user { 'luke':
     home => '/home/luke',
     uid => '100',
     ensure => 'present',
     comment => 'Luke Kanies,,,',
     gid => '1000',
     shell => '/bin/bash',
     groups => ['sysadmin','audio','video','puppet']
    }

## AUTHOR
Luke Kanies

## COPYRIGHT
Copyright (c) 2011 Puppet Inc., LLC Licensed under the Apache 2.0
License