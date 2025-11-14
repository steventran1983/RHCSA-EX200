# Gain Superuser Access

# Manageing Local User

## usermod Options

| Option | Usage |
|--------|-------|
| -a, --append | Use it with the -G option to add the supplementary groups to the user's current set of group memberships instead of replacing the set of supplementary groups with a new set. |
| -c, --comment COMMENT | Add the COMMENT text to the comment field. |
| -d, --home HOME_DIR | Specify a home directory for the user account. |
| -g, --gid GROUP | Specify the primary group for the user account. |
| -G, --groups GROUPS | Specify a comma-separated list of supplementary groups for the user account. |
| -L, --lock | Lock the user account. |
| -m, --move-home | Move the user's home directory to a new location. You must use it with the -d option. |
| -s, --shell SHELL | Specify a particular login shell for the user account. |
| -U, --unlock | Unlock the user account. |

```


[root@host ~]# date +%F 1
2022-03-10
[root@host ~]# date -d "+30 days" +%F 2
2022-04-09
[root@host ~]# chage -E $(date -d "+30 days" +%F) cloudadmin10 3
[root@host ~]# chage -l cloudadmin10 | grep "Account expires" 4
Account expires						: Apr 09, 2022


The nologin Shell
The nologin shell acts as a replacement shell for the user accounts that are not intended to log in interactively to the system. It is good security practice to disable an account from logging in to the system when the account does not require it. For example, a mail server might require an account to store mail and a password for the user to authenticate with a mail client to retrieve mail. That user does not need to log in directly to the system.

A common solution to this situation is to set the user's login shell to /sbin/nologin. If the user attempts to log in to the system directly, then the nologin shell closes the connection.

[root@host ~]# usermod -s /sbin/nologin newapp
[root@host ~]# su - newapp
Last login: Wed Feb  6 17:03:06 IST 2019 on pts/0
This account is currently not available.