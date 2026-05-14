# Runbook: Restore a VM from Proxmox Backup Server

<!-- RU: Runbook = пошаговая инструкция "что делать, когда что-то надо сделать или сломалось".
     Особенно полезно в стрессе, когда уже что-то упало и думать тяжело. -->

**Goal:** restore a VM on `n5` from a backup stored on the `pbs` VM.

**When to use:** VM is corrupted, accidentally deleted, or needs to be rolled
back to a previous state.

## Prerequisites

- PBS VM (`pbs`, 192.168.1.11) is reachable from the Proxmox host.
- The PBS datastore is mounted and healthy.
- You know which VMID and which backup snapshot you want to restore.

## Procedure

1. **Identify the backup.** In the Proxmox web UI:
   `Datacenter → Storage → pbs → Content`. Find the snapshot by VMID and date.

2. **Stop the current VM** (if it still exists) to avoid conflicts:
   ```
   qm stop <VMID>
   ```

3. **Trigger the restore.** From the Proxmox web UI, select the snapshot and
   click `Restore`. Choose:
   - **Storage:** where the restored disks should land (e.g. `local-lvm`).
   - **VMID:** same as original, or new one if you want to keep both.
   - **Unique:** check this if you're creating a new VM to avoid MAC conflicts.

4. **Wait for the task to finish.** Watch the task log at the bottom of the UI.

5. **Verify.** Boot the VM, log in, check that the expected data and services
   are present.

## Rollback

If the restored VM is broken, you can re-run the restore from an earlier
snapshot. PBS keeps multiple snapshots according to the retention policy.

## See also

- [Proxmox Backup Server docs](https://pbs.proxmox.com/docs/)
