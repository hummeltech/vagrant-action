# any VM Action

**The value for [runs-on](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idruns-on) should be set to either `macos-latest` or `ubuntu-latest` in order to use this action.**

This action allows the running of command-line programs via the `bash` shell of VMs provisioned with any VM using the [run](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idstepsrun) keyword. This also works with composite actions which exclusively use the `run` keyword (and/or call other composite actions which also do so.)

#### *This action is currently only tested with these os values (but will probably also work with others [see [here](https://github.com/anyvm-org/anyvm) for options]):*
  * `alpine`

# Usage
<!-- start usage -->
1. Provision a `VM` using the specified `os` (with 2 CPUs & 2GB of RAM)
    ```yaml
    - name: Provision VM
      uses: hummeltech/vagrant-action@v3
      with:
        os: alpine
        cpu: 2
        mem: 2048
    ```
2. Execute a command using the `run` keyword
    ```yaml
    - name: Display the contents of /etc/os-release
      run: cat /etc/os-release
    ```
<!-- end usage -->


# Breaking changes in v3+

### This action previously used vagrant, but now uses [anyvm.py](https://github.com/anyvm-org/anyvm)

You will need to modify any `with` values in order to upgrade to `v3` and above, see [here](./action.yml) for available inputs.

Using `v2` with public boxes from [HCP Vagrant](https://portal.cloud.hashicorp.com/vagrant/discover) should continue to work until November 2, 2026.

Using `v2` with self-hosted boxes should continue to work using `with: vagrant_box_descriptor: {public box URL}`.

> HCP Vagrant is being deprecated and limited features will be available from the community edition effective November 2, 2026. Most notably this change will now require customers using Vagrant boxes to be responsible for the hosting costs incurred on given providers.

See [here](https://developer.hashicorp.com/hcp/docs/vagrant/hcp-vagrant-eol) for more details.
