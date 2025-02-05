# Ansible Role: Server Preparation

This role prepares a server for operation by:
- Encrypting the second disk (automatically detected).
- Disabling CPU C-states.
- Setting CPU performance mode.
- Renaming the network interface to `net0`.
- Displaying CPU and Hyper-Threading information.

## Requirements
- **Second Disk**: Attached to the server (e.g., `/dev/xvdf`).
- **Ansible**: Version 2.9 or higher.
- **SSH Access**: Configured with key-based authentication.

## Variables
**Variables stored in ./roles/server-prep/defaults/main.yml**

| Variable              | Default         | Description                                                                 |
|-----------------------|-----------------|-----------------------------------------------------------------------------|
| `encrypted_disk`      | `/dev/xvdf`    | Path to the second disk to encrypt.                                         |
| `encrypted_partition` | `/dev/xvdf1`   | Partition to encrypt (created if missing).                                  |
| `mount_point`         | `/data`        | Mount path for the encrypted partition (optional).                          |
| `mount_enabled`       | `false`        | Set to `true` to enable mounting.                                           |


## Usage
1. Add your server to the inventory file (`inventory/hosts`):
   ```ini
   [servers]
   server1 ansible_host={IP} ansible_user={USER}
   ```
2. Run the playbook:
   ```bash
   ansible-playbook -i inventory/hosts playbook.yml
   ```