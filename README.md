# ansible_role_framework_tmux

An Ansible role framework that assists with managing detached shell sessions with Tmux.

## Requirements

* Tmux

## Role Variables

* tmux_name = The Tmux session name to target.
* tmux_state = The state that the Tmux session should be in.
    * present = Create a detached Tmux session.
    * absent = Remove an existing Tmux session.
    * execute = Execute a command on an existing Tmux session.
* tmux_cmd = The command to execute in the Tmux session when the state is "present" or "execute".

## Dependencies

None.

## Example Playbook

An example playbook is provided at `tests/test.yml`. It uses tags to avoid some tasks that the end-user may not want to run.

Create a new Tmux session and skip the deletion:

```
$ ansible-playbook --skip-tags tmux_absent tests/test.yml
```

Skip the creation and deletion steps. Only execute commands.

```
$ ansible-playbook --skip-tags tmux_create --skip-tags tmux_absent tests/test.yml
```

Only delete the Tmux session.

```
$ ansible-playbook --tags tmux_absent tests/test.yml
```

## License

Apache v2.0
