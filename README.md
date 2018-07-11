# shell-do-undo

A Clojure library designed to provide a simple Lisp DSL that handles --hacks--:

* Transpiling of "fact", based on chosen destination shell implementation dialect:
  * "fact" setup script
  * "fact" purge script
  * "fact" update script
    * with respect to updates of "fact"'s "aspects". For example:
      * In some edge cases , update in one service demand an restart of "observer" service, an good example is:
        * update of `fluentd` agent's config, that uses `syslog` as a base "input" bus, needs an restart of `syslog/rsyslog` service.
* "fact" state management methodology
  * with resect to "parent system's" concepts, and "system's life cycle" phases implementation envelope. For example like in:
    * OS service level concepts
      * linux
      * *nix
      * windows
    * IaaS
      * AWS
        * **elasticbenstalk**
        * **ECS**
        * *EKS* ???
      * Google
        * App Engine ?
      * Azure
        * WFT ?
    * PaaS
      * Heroku
      * google app engine
      * AWS
        * EKS ?
        * ECS ?
        * EBeanstak?
## Usage

* DSL transpiles an "fact", into a "playbook" shell script bundle that MUST have following interface:
  * "fact" setup
  * "fact" purge

## Goals

* solve an "scope issue" for "high-level" language adepts by:
  * removing an "learning curve" related to variables scope management in shell
    * a good example is refactoring an sequential script part into a `function`
      * for "high level" leanguages , function should handle `arguments` and return a `value`.
        * with `shell` related dialects you usualy need to handle a stack in some scope/way.
  * establishing an `syntax` to handle `setup/purge` triggering based on "source of truth" change
    * `S/P` phase must be triggered on:
      * Demand - change in "Parent system" state
        * for example : `eb deploy`
      * Change in the "source of truth"
        * for example: there is fluentd agent, the config is changed, aganet should upgrade local config, and restart the "fact" service;
* keeps state of **facts** in relation to their **nature**, like in case of:
  * installed package
  * copied file
  * etc
    * for and @ideas, see [`bork`](https://github.com/mattly/bork)

## License

Copyright © 2018 MIT

