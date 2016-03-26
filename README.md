.h1 If you want to run local automation steps and not have to supply password

* Create a ansible vault secret file. From the top-level Genesis dir

```ansible-vault create secret```

* Make a note of the vault password. The editor will come up and add:

```ansible_become_pass: yoursudopassword```

* With the password you used to create the ```secret``` file, create a text file in ```~/.ansbile/``` called ```~/.ansible/vault.txt``` with just the password in that file. Set permissions 700.

* IMPORTANT: If instead of using ansible-vault, you want to instead
  use a password-less sudo for the user running ansible locally,
  comment out ```:use_vault: true``` in ```.vagrant/cluster-inventory```
  example:

```
[default]
:use_vault false
```
* You will need to also make sure to provide the arguments to ansible to use
  the vault secret

```EXTRA_OPTS=--vault-password-file=~/.ansible/vault.txt```

.h1 Alternative -- install passlib locally

Either in a python virtualenv or sudo:

pip install passlib
