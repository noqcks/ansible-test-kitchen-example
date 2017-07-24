## Ansible Test Kitchen Example

[![Build Status Master](https://travis-ci.org/bob5ec/ansible-test-kitchen-exmaple.svg?branch=master)](https://travis-ci.org/bob5ec/ansible-test-kitchen-exmaple)

We can use [test-kitchen](https://github.com/test-kitchen/test-kitchen) with [serverspec](http://serverspec.org/) to run some basic tests for our ansible roles.

Test kitchen allows us to do the following

```
1. spin up docker container
2. provision container using ansible role
3. test that our ansible role did everything we wanted it to
```

The files contained in this repo should be enough to get you easily started with testing ansible roles using serverspec.

##### 0. `requirements.yml`

This are the dependencies listed in meta/main of your ansible role. If there are no dependecies, remove `requirements_path:` from `.kitchen.yml`

##### 1. `.travis.yml`

Describes how to run everything on travis-ci. If you are not using travis-ci, you can omit this file.

##### 2. `.kitchen.yml`

Describes what to run our serverspec tests on (docker, vagrant, ec2), and how to provision our hosts.

##### 3. `/test/integration/serverspec/default.yml`

This is the ansible playbook we run to provision our hosts. The most basic function is just installing our ansible role on the host machine.

##### 4. `/test/integration/serverspec/localhost/default_spec.rb`

This is the serverspec file that contains the tests to run against our hosts. For resource types see the [documentation](http://serverspec.org/resource_types.html).

