# xbps ansible module

Manage packages with the XBPS package manager.
## Requirements
* Ansible

## Options
	name:
		description:
			- Name of the package to install, upgrade, or remove.
		required: false
		default: null
	state:
		description:
			- Desired state of the package.
		required: false
		default: "present"
		choices: ["present", "absent", "latest"]
	recurse:
		description:
			- When removing a package, also remove its dependencies, provided
			  that they are not required by other packages and were not
			  explicitly installed by a user.
		required: false
		default: no
		choices: ["yes", "no"]
	update_cache:
		description:
			- Whether or not to refresh the master package lists. This can be
			  run as part of a package installation or as a separate step.
		required: false
		default: no
		choices: ["yes", "no"]
	upgrade:
		description:
			- Whether or not to upgrade whole system
		required: false
		default: no
		choices: ["yes", "no"]

## EXAMPLES
	# Install package foo
	- xbps: name=foo state=present
	# Upgrade package foo
	- xbps: name=foo state=latest update_cache=yes
	# Remove packages foo and bar
	- xbps: name=foo,bar state=absent
	# Recursively remove package foo
	- xbps: name=foo state=absent recurse=yes
	# Update package cache
	- xbps: update_cache=yes
	# Upgrade packages
	- xbps: upgrade=yes

## Authors:
* "Dino Occhialini (@dinoocch)"
* "Michael Aldridge (@the-maldridge)"
