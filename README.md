## LinuxAid Config

### Directory Structure.

* `agents` will hold your node hiera config

  ```raw
  # ls -al agents/
  -rw-rw-r-- 1 foo users 16803 Sep 11 12:04 web01.domain.yaml
  -rw-rw-r-- 1 foo users  7811 Sep 11 12:04 haproxy01.domain.yaml
  drwxrwxr-x 2 foo users  4096 Sep  5 13:10 tags
  ```

* `tags` will hold your tags hiera config, which is a grouping of nodes of same business roles, or location or anything that you like to group the nodes.

  ```raw
  ls -al agents/tags/
  -rw-rw-r-- 1 foo users   321 Aug 16  2024 dk.yaml
  ```

* `global.yaml` is the global file, which will be applied to all the nodes across the infrastructure.

  ```yaml
  ---
  common::system::time::timezone: "Europe/Copenhagen"
  common::system::dns::nameservers:
    - "10.0.3.21"
  common::system::users:
    obmondo:
      realname: "Obmondo Admin"
      uid: 3000
      password_hash: "$6$BnWHAEch$l3WTl2eA.Cbb.oOBEb3tUG."
      sudoroot: true
      ssh_authorized_keys:
        - "ssh-rsa AAAAB3NzaC1yfshVHrzY61IeSbWhQ== cardno:000474912423"
  ```

### Puppet Modules

* You can add your own modules in the linuxaid-config and it will be picked up by the puppetserver automatically.

  ```raw
  ls -al modules/customers/
  total 24
  drwxrwxr-x 5 foo users 4096 Dec  9  2024 .
  drwxrwxr-x 3 foo users 4096 Aug 16  2024 ..
  drwxrwxr-x 3 foo users 4096 Aug 16  2024 data
  drwxrwxr-x 3 foo users 4096 Jan 30  2025 files
  -rw-rw-r-- 1 foo users  528 Aug 16  2024 hiera.yaml
  drwxrwxr-x 3 foo users 4096 Aug 16  2024 lib
  ```
