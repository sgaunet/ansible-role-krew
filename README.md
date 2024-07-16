
# Ansible Role: krew

[![CI](https://github.com/sgaunet/ansible-role-krew/workflows/CI/badge.svg)](https://github.com/sgaunet/ansible-role-krew/actions?query=workflow%3ACI)

An Ansible Role that installs [krew][https://github.com/kubernetes-sigs/krew] on Linux.

## Requirements

kubectl should be setup. **This role will fail if kubectl is not found in the PATH.**
You can setup kubectl with this role: [sgaunet.kubectl](https://github.com/sgaunet/ansible-role-gh-release-installer)

Example:

```yaml
- name: Install kubectl
  ansible.builtin.import_role:
    name: sgaunet.gh_role_installer
    defaults_from: "kubectl"
  # override the following vars if needed:
  # vars:
  #   gh_role_installer_version: "{{ kubectl_version }}"
  #   gh_role_installer_os: "{{ kubectl_os }}"
  #   gh_role_installer_arch: "{{ kubectl_arch }}"
```

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    krew_version: "latest"     # Version of krew to install. Use "latest" to install the latest version.
    krew_bin_path: "/usr/local/bin"
    krew_tmp_directory: "{{ lookup('env', 'TMPDIR') | default('/tmp', true) }}"
    krew_os: "linux"
    krew_arch: "amd64"

## Dependencies

kubectl should be setup. **This role will fail if kubectl is not found in the PATH.**

## Example Playbook

You need the role sgaunet.gh_role_installer: `ansible-galaxy install sgaunet.gh_role_installer`

```yaml
- hosts: all
  roles:
    - sgaunet.krew
```

## License

MIT
