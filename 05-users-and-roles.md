# Users and Roles

## Users

In Sensu users are a resource that represents a person or thing that has access
to your system.

### Default User

By default, your Sensu installation comes with a single user named `admin`. This
user has the password `P@ssw0rd!` and it is **strongly** recommended that you
change it immediately. To do so, you'll first want to authenticate using the
`sensuctl` tool.

> sensuctl configure
```sh
? Sensu Base URL: http://my-sensu-host:8080
? Username: admin
? Password:  *********
? ...
```

Once authenticated, you can use the `change-password` command.

> sensuctl user change-password
```sh
? Current Password:  *********
? Password:          *********
? Confirm:           *********
```

### View Users

To view all the users, that your account has access to see.

> sensuctl user list
```sh
   Username      Roles   Enabled
─────────────── ─────── ─────────
 admin           admin   true
 deanlearner     admin   true
 garthmarenghi   admin   true
 lizasher        admin   false
```

### Managing Users

You can easily add users through the CLI tool.

<img src="./assets/sensuctl-user-create.gif" alt="create user" width="500px" />

Alternatively the CLI tool has a non interactive option as well.

```sh
sensuctl user create garthmarenghi --password darkplace123
sensuctl user create deanleaner --admin --password passw0rd # easily make them an admin
sensuctl user create juliensanchez --roles viewer,agent --password passw0rd # apply roles
```

If you need to disable a user, you can simply use the `disable` subcommand.

```sh
sensuctl user disable lizasher
```

However, later if you would like to reinstate their account.

```sh
sensuctl user reinstate lizasher
```

## Roles

The initial installation of Sensu includes an initial `admin` role that gives an
user associated with it full access to the system.

Further, you can easily create more roles that give as much (or as little) access
as you see fit.

### Viewing Roles

To view all the roles currently configured in your Sensu installation. Run the
following:

```sh
sensuctl role list
```

To view all the rules configured for a role.

```sh
sensuctl role list-rules MY-ROLE
```

#### Example

<img src="./assets/sensuctl-role-list.gif" alt="sensuctl list roles" width="500px" />

### Managing Roles

To add a new role, simply call the `sensuctl` role create command with it's
intended name.

```sh
sensuctl role create dreamweaver
```

To add rules to the role, use the `add-rule` subcommand.

```sh
sensuctl role add-rule dreamweaver --type events --read
sensuctl role add-rule dreamweaver -t checks -crud      # short hand
```

To remove a rule from the role, pass the role and rule type to the `remove-rule`
subcommand.

```sh
sensuctl role remove-rule dreamweaver checks
```

Finally, to remove a role from the system run the `delete` subcommand.

```sh
sensuctl role delete dreamweaver
```

#### Example

<img src="./assets/sensuctl-role-manage.gif" alt="sensuctl list roles" width="500px" />


### Managing User Roles

If you would like to add a role to an existing user, the `add-role` user
subcommand can do just that.

```sh
sensuctl user add-role garthmarenghi admin
```

Easy cometh, easy goeth. Removing a role is just as easy.

```sh
sensuctl user remove-role garthmarenghi admin
```
