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


## Usage

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

```
$ ./bin/librarian-chef install
```

----
WIP