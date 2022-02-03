# Ansible Collection - jwerak.collection_test

This is a test collection to demonstrate mounting of collection from subdirectory of collection (e.g. playbooks).

The goal is to have test playbooks e.g. in playbooks directory which would test or demonstrate usage of collection in execution environment.

This collection is stored under ansible_collections path: `/home/jveverka/git/jwerak/ansible/ansible_collections/jwerak/collection_test` on my localhost.

I am trying to list collections available in execution environment using command `ansible-navigator collections --log-level debug`, but the result is:

```
humph. no collections were found in the following paths:
- /home/jveverka/git/jwerak/ansible/ansible_collections/jwerak/collection_test/playbooks/collections (bind_mount)
- /home/jveverka/git/jwerak/ansible (contained)
...
```

I've checked the logs and I didn't see the volume being mounted with `-v` option: 

```
211216214720.810 DEBUG 'ansible-runner.wrap_args_for_containerization' container engine invocation: podman run --rm --tty --interactive -v /home/jveverka/git/jwerak/ansible/ansible_collections/jwerak/collection_test/playbooks/:/home/jveverka/git/jwerak/ansible/ansible_collections/jwerak/collection_test/playbooks/ --workdir /home/jveverka/git/jwerak/ansible/ansible_collections/jwerak/collection_test/playbooks -v /run/user/1000/keyring/:/run/user/1000/keyring/ -e SSH_AUTH_SOCK=/run/user/1000/keyring/ssh -v /home/jveverka/.ssh/:/home/runner/.ssh/ --group-add=root --ipc=host -v /tmp/ansible-navigator_2srao4qv/artifacts/:/runner/artifacts/:Z -v /tmp/ansible-navigator_2srao4qv/:/runner/:Z -v /home/jveverka/.local/share/ansible_navigator/utils/:/home/jveverka/.local/share/ansible_navigator/utils/ -v /home/jveverka/.cache/ansible-navigator/:/home/jveverka/.cache/ansible-navigator/:z --env-file /tmp/ansible-navigator_2srao4qv/artifacts/d51573a4-ad01-4095-92f5-a221b7911886/env.list --quiet --name ansible_runner_d51573a4-ad01-4095-92f5-a221b7911886 registry.redhat.io/ansible-automation-platform-21/ee-supported-rhel8:1.0.0-30 python3 /home/jveverka/.local/share/ansible_navigator/utils/catalog_collections.py -a /home/jveverka/git/jwerak/ansible/ansible_collections/jwerak/collection_test/playbooks/collections -c /home/jveverka/.cache/ansible-navigator/collection_doc_cache.db
211216214720.810 DEBUG 'ansible-runner._handle_command_wrap' command: podman run --rm --tty --interactive -v /home/jveverka/git/jwerak/ansible/ansible_collections/jwerak/collection_test/playbooks/:/home/jveverka/git/jwerak/ansible/ansible_collections/jwerak/collection_test/playbooks/ --workdir /home/jveverka/git/jwerak/ansible/ansible_collections/jwerak/collection_test/playbooks -v /run/user/1000/keyring/:/run/user/1000/keyring/ -e SSH_AUTH_SOCK=/run/user/1000/keyring/ssh -v /home/jveverka/.ssh/:/home/runner/.ssh/ --group-add=root --ipc=host -v /tmp/ansible-navigator_2srao4qv/artifacts/:/runner/artifacts/:Z -v /tmp/ansible-navigator_2srao4qv/:/runner/:Z -v /home/jveverka/.local/share/ansible_navigator/utils/:/home/jveverka/.local/share/ansible_navigator/utils/ -v /home/jveverka/.cache/ansible-navigator/:/home/jveverka/.cache/ansible-navigator/:z --env-file /tmp/ansible-navigator_2srao4qv/artifacts/d51573a4-ad01-4095-92f5-a221b7911886/env.list --quiet --name ansible_runner_d51573a4-ad01-4095-92f5-a221b7911886 registry.redhat.io/ansible-automation-platform-21/ee-supported-rhel8:1.0.0-30 python3 /home/jveverka/.local/share/ansible_navigator/utils/catalog_collections.py -a /home/jveverka/git/jwerak/ansible/ansible_collections/jwerak/collection_test/playbooks/collections -c /home/jveverka/.cache/ansible-navigator/collection_doc_cache.db
```

Full log at [log.txt](./log.txt).
