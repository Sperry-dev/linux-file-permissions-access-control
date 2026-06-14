# Linux File Permissions & Access Control

## Scenario

A sensitive project file needed to be protected from unauthorized access while allowing access through group membership when permissions were modified.

## Objective

Configure file ownership and permissions, test access restrictions, and verify access after modifying permissions.

## Commands Used

```bash
sudo groupadd devteam
sudo useradd -m -s /bin/bash alice
sudo useradd -m -s /bin/bash bob
sudo usermod -aG devteam alice
sudo usermod -aG devteam bob
sudo mkdir -p /srv/project
echo "Top Secret Project File" | sudo tee /srv/project/data.txt
sudo chown :devteam /srv/project/data.txt
sudo chmod 600 /srv/project/data.txt
```

## Verification

Initial permissions:

```text
-rw------- 1 root devteam 24 Jun 14 01:15 /srv/project/data.txt
```

Access denied:

```text
alice@ubuntu:~$ cat /srv/project/data.txt
cat: /srv/project/data.txt: Permission denied
```

Modified permissions:

```text
-rw-r----- 1 root devteam 24 Jun 14 01:15 /srv/project/data.txt
```

Access granted:

```text
alice@ubuntu:~$ cat /srv/project/data.txt
Top Secret Project File
```

## Skills Demonstrated

- Linux Administration
- User Management
- Group Management
- File Permissions
- Access Control
- Linux Troubleshooting
- Security Principles
<img width="567" height="537" alt="Screenshot 2026-06-13 at 8 22 34 PM" src="https://github.com/user-attachments/assets/83b04ffd-9a2d-406a-973c-ea1583312b74" />
