# Getting Started knife-zero with test-kitchen.

Write recipe once.

## Overview

- Chef(Knife)
    - create your recipes.
    - manages your remote nodes.
- Librarian-Chef
    - collect remote cookbooks.
    - manage remote and local cookbooks.
- Test-kitchen
    - execute recipes on Vagrant.
    - test with Serverspec(optional).
- Knife-Zero
    - execute recipes on remote nodes.


## Flow

1. Install gems by Bundler.
1. Write your recipe.
1. Collect remote cookbooks by Librarian-Chef into your workstation.
1. Converge and test cookbooks with test-kitchen.
1. Update remote nodes by knife-zero.


## Example

How to use this repository.

### Bundler

Install RubyGems and cli.

```
$ bundle install --binstubs --path=vendor/bundle

$ ls ./bin/
chef-apply		chef-solo		ffi-yajl-bench		ldiff			pry			shef
chef-client		chef-zero		htmldiff		librarian-chef		rackup			thor
chef-service-manager	coderay			kitchen			minitar			restclient
chef-shell		erubis			knife			ohai			safe_yaml
```


### Librarian-Chef

Collect remote cookbooks referd to `Cheffile`.

```
$ ./bin/librarian-chef install

$ ls cookbooks/
build-essential
```

----

### Test-kitchen

Execute recipes on Vagrant VirtualMachine.

RunList and Attributes are defined by `.kitchen.yml`.


```
$ ./bin/kitchen converge
-----> Starting Kitchen (v1.2.1)
-----> Converging <default-ubuntu-1404>...
       Preparing files for transfer
       Resolving cookbook dependencies with Librarian-Chef 0.0.4...
       Removing non-cookbook files before transfer
       Preparing nodes
       Transfering files to <default-ubuntu-1404>
[2014-12-28T04:22:37+00:00] INFO: Started chef-zero at http://localhost:8889 with repository at /tmp/kitchen, /tmp/kitchen       
  One version per cookbook       
       
[2014-12-28T04:22:37+00:00] INFO: Forking chef instance to converge...       
Starting Chef Client, version 12.0.3       
[2014-12-28T04:22:37+00:00] INFO: *** Chef 12.0.3 ***       
[2014-12-28T04:22:37+00:00] INFO: Chef-client pid: 5743       
[2014-12-28T04:22:43+00:00] WARN: Child with name 'dna.json' found in multiple directories: /tmp/kitchen/dna.json and /tmp/kitchen/dna.json       
[2014-12-28T04:22:43+00:00] INFO: Setting the run_list to ["build-essential::default", "start::default"] from CLI options       
[2014-12-28T04:22:43+00:00] INFO: Run List is [recipe[build-essential::default], recipe[start::default]]       
[2014-12-28T04:22:43+00:00] INFO: Run List expands to [build-essential::default, start::default]       
[2014-12-28T04:22:43+00:00] INFO: Starting Chef Run for default-ubuntu-1404       
[2014-12-28T04:22:43+00:00] INFO: Running start handlers       
[2014-12-28T04:22:43+00:00] INFO: Start handlers complete.       
[2014-12-28T04:22:43+00:00] INFO: HTTP Request Returned 404 Not Found : Object not found: /reports/nodes/default-ubuntu-1404/runs       
resolving cookbooks for run list: ["build-essential::default", "start::default"]       
[2014-12-28T04:22:43+00:00] INFO: Loading cookbooks [build-essential@2.1.3, start@0.1.0]       
Synchronizing Cookbooks:       
  - start       
  - build-essential       
Compiling Cookbooks...       
Converging 7 resources       
Recipe: build-essential::_debian       
  * apt_package[autoconf] action install[2014-12-28T04:22:43+00:00] INFO: Processing apt_package[autoconf] action install (build-essential::_debian line 21)       
 (up to date)       
  * apt_package[binutils-doc] action install[2014-12-28T04:22:44+00:00] INFO: Processing apt_package[binutils-doc] action install (build-essential::_debian line 22)       
 (up to date)       
  * apt_package[bison] action install[2014-12-28T04:22:44+00:00] INFO: Processing apt_package[bison] action install (build-essential::_debian line 23)       
 (up to date)       
  * apt_package[build-essential] action install[2014-12-28T04:22:44+00:00] INFO: Processing apt_package[build-essential] action install (build-essential::_debian line 24)       
 (up to date)       
  * apt_package[flex] action install[2014-12-28T04:22:44+00:00] INFO: Processing apt_package[flex] action install (build-essential::_debian line 25)       
 (up to date)       
  * apt_package[gettext] action install[2014-12-28T04:22:44+00:00] INFO: Processing apt_package[gettext] action install (build-essential::_debian line 26)       
 (up to date)       
  * apt_package[ncurses-dev] action install[2014-12-28T04:22:44+00:00] INFO: Processing apt_package[ncurses-dev] action install (build-essential::_debian line 27)       
[2014-12-28T04:22:44+00:00] INFO: apt_package[ncurses-dev] is a virtual package, actually acting on package[libncurses5-dev]       
 (up to date)       
[2014-12-28T04:22:44+00:00] INFO: Chef Run complete in 0.509730805 seconds       
       
Running handlers:       
[2014-12-28T04:22:44+00:00] INFO: Running report handlers       
Running handlers complete       
[2014-12-28T04:22:44+00:00] INFO: Report handlers complete       
Chef Client finished, 0/7 resources updated in 6.781036641 seconds       
       Finished converging <default-ubuntu-1404> (0m9.83s).
-----> Converging <default-centos-65>...
       Preparing files for transfer
       Resolving cookbook dependencies with Librarian-Chef 0.0.4...
       Removing non-cookbook files before transfer
       Preparing nodes
       Transfering files to <default-centos-65>
zlib(finalizer): the stream was freed prematurely.
       [2014-12-28T04:22:47+00:00] INFO: Started chef-zero at http://localhost:8889 with repository at /tmp/kitchen, /tmp/kitchen
         One version per cookbook
       
       [2014-12-28T04:22:47+00:00] INFO: Forking chef instance to converge...
       Starting Chef Client, version 12.0.3
       [2014-12-28T04:22:47+00:00] INFO: *** Chef 12.0.3 ***
       [2014-12-28T04:22:47+00:00] INFO: Chef-client pid: 2950
       [2014-12-28T04:22:49+00:00] WARN: Child with name 'dna.json' found in multiple directories: /tmp/kitchen/dna.json and /tmp/kitchen/dna.json
       [2014-12-28T04:22:49+00:00] INFO: Setting the run_list to ["build-essential::default", "start::default"] from CLI options
       [2014-12-28T04:22:49+00:00] INFO: Run List is [recipe[build-essential::default], recipe[start::default]]
       [2014-12-28T04:22:49+00:00] INFO: Run List expands to [build-essential::default, start::default]
       [2014-12-28T04:22:49+00:00] INFO: Starting Chef Run for default-centos-65
       [2014-12-28T04:22:49+00:00] INFO: Running start handlers
       [2014-12-28T04:22:49+00:00] INFO: Start handlers complete.
       [2014-12-28T04:22:49+00:00] INFO: HTTP Request Returned 404 Not Found : Object not found: /reports/nodes/default-centos-65/runs
       resolving cookbooks for run list: ["build-essential::default", "start::default"]
       [2014-12-28T04:22:49+00:00] INFO: Loading cookbooks [build-essential@2.1.3, start@0.1.0]
       Synchronizing Cookbooks:
         - start
         - build-essential
       Compiling Cookbooks...
       Converging 9 resources
       Recipe: build-essential::_rhel
         * yum_package[autoconf] action install[2014-12-28T04:22:49+00:00] INFO: Processing yum_package[autoconf] action install (build-essential::_rhel line 21)
        (up to date)
         * yum_package[bison] action install[2014-12-28T04:22:50+00:00] INFO: Processing yum_package[bison] action install (build-essential::_rhel line 22)
        (up to date)
         * yum_package[flex] action install[2014-12-28T04:22:50+00:00] INFO: Processing yum_package[flex] action install (build-essential::_rhel line 23)
        (up to date)
         * yum_package[gcc] action install[2014-12-28T04:22:50+00:00] INFO: Processing yum_package[gcc] action install (build-essential::_rhel line 24)
        (up to date)
         * yum_package[gcc-c++] action install[2014-12-28T04:22:50+00:00] INFO: Processing yum_package[gcc-c++] action install (build-essential::_rhel line 25)
        (up to date)
         * yum_package[kernel-devel] action install[2014-12-28T04:22:50+00:00] INFO: Processing yum_package[kernel-devel] action install (build-essential::_rhel line 26)
        (up to date)
         * yum_package[make] action install[2014-12-28T04:22:50+00:00] INFO: Processing yum_package[make] action install (build-essential::_rhel line 27)
        (up to date)
         * yum_package[m4] action install[2014-12-28T04:22:50+00:00] INFO: Processing yum_package[m4] action install (build-essential::_rhel line 28)
        (up to date)
         * yum_package[patch] action install[2014-12-28T04:22:50+00:00] INFO: Processing yum_package[patch] action install (build-essential::_rhel line 29)
        (up to date)
       [2014-12-28T04:22:50+00:00] INFO: Chef Run complete in 1.490272393 seconds
       
       Running handlers:
       [2014-12-28T04:22:50+00:00] INFO: Running report handlers
       Running handlers complete
       [2014-12-28T04:22:50+00:00] INFO: Report handlers complete
       Chef Client finished, 0/9 resources updated in 3.165634097 seconds
       Finished converging <default-centos-65> (0m6.55s).
-----> Kitchen is finished. (0m16.71s)
zlib(finalizer): the stream was freed prematurely.
```


### Knife-Zero

See: https://github.com/higanworks/knife-zero
