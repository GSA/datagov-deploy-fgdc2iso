[![CircleCI](https://circleci.com/gh/GSA/datagov-deploy-fgdc2iso.svg?style=svg)](https://circleci.com/gh/GSA/datagov-deploy-fgdc2iso)

# datagov-deploy-fgdc2iso

Ansible role to deploy fgdc2iso for the Data.gov platform. Endpoint `/fgdc2iso` provides service for transformations from FGDC/RSE to ISO 19115-2.

## Usage

Include this role in your `requirements.yml`.

```yaml
- src: https://github.com/gsa/datagov-deploy-fgdc2iso.git
```

The role depends on having Tomcat installed. We recommend including the role
`robertdebock.tomcat`  and its dependency roles.

Example playbook:

```yaml
---
- name: FGDC2ISO
  hosts: fdgc2iso
  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.core_dependencies
    - role: robertdebock.java
    - role: robertdebock.tomcat
      vars:
        tomcat_instances:
          - name: "tomcat"
            version: 9
    - role: gsa.datagov-deploy-fgdc2iso
```

### Variables

See [robertdebock.tomcat](https://github.com/robertdebock/ansible-role-tomcat/blob/master/README.md) for
additional variables.

Above sample variables will install Tomcat 9 to `/opt/tomcat/`, and fdgc2iso.war
file will be deployed to `/opt/tomcat/webapps/fdgc2iso/`.


## Prerequisites for development

- [Docker](https://www.docker.com/)
- [Python](https://www.python.org/) 3.6
- [Pipenv](https://pipenv.readthedocs.io/en/latest/)


## Development

### Requirements

- [Docker](https://www.docker.com/get-started)
- [Pipenv](https://pipenv.readthedocs.io/en/latest/)
- [Python](https://www.python.org) v3.6


### Setup

Pipenv creates a virtualenv for you and installs the python dependencies.

    $ pipenv install --dev

Then you can run commands with pipenv.

    $ pipenv run molecule converge

Or, you can activate the virtualenv in your shell so you don't have to run pipenv
all the time.

    $ pipenv shell


### Run the tests

Run the tests with [molecule](https://molecule.readthedocs.io/en/latest/).

    $ pipenv run molecule test --all

If you're new to molecule, see our
[wiki](https://github.com/GSA/datagov-deploy/wiki/Developing-Ansible-roles-with-Molecule)
for a quick primer.


## Contributing

See [CONTRIBUTING](CONTRIBUTING.md) for additional information.


## Public domain

This project is in the worldwide [public domain](LICENSE.md). As stated in [CONTRIBUTING](CONTRIBUTING.md):

> This project is in the public domain within the United States, and copyright and related rights in the work worldwide are waived through the [CC0 1.0 Universal public domain dedication](https://creativecommons.org/publicdomain/zero/1.0/).
>
> All contributions to this project will be released under the CC0 dedication. By submitting a pull request, you are agreeing to comply with this waiver of copyright interest.
