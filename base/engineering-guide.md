# Base Engineering Guide

This guide defines common engineering concepts: canonical commands, validation tiers, local vs CI validation, release validation, and implementation-agent expectations.

Core principles:

```text
Commands are canonical.
Validation is tiered.
Implementation validation is not always release validation.
CI is the integration authority when configured.
Documentation sync is separate from implementation.
```

Recommended base commands:

```text
./eng/restore.sh
./eng/build.sh
./eng/test.sh
./eng/check.sh
```
