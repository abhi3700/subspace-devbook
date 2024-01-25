# info

This command displays info about the farmer instance (i.e. total amount of rewards, and status of initial plotting)

## Usage

TODO: Add CLI output for an active farmer instance

---

If there is no farmer instance running, the following error will be displayed:

```bash
$ pulsar info
There is no active farmer instance...
Error: couldn't open existing summary file

Caused by:
    No such file or directory (os error 2)

Location:
    src/summary.rs:111:14
```

This is generally expected when you are running `pulsar` for the first time and node syncing is not yet complete.

```bash
$ pulsar farm
Starting node ...
Node started successfully!
 ◝  [00:02:34] 30% [] (377167/1253100) 0.00bps, syncing, ETA: 1705305d 15:54:51
```

## Demystify
