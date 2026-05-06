dummy-user-generator
================================================================================

CLI tool for rapidly generating random lists of Japanese users.
Supports multi-threading parallel generation and parallel CSV writing.

It can generate up to 10 million records at a time,
but as this requires 1.5 to 2 GB of disk space,
please adjust the number of records to be generated accordingly.

> [!NOTE]
> This software is based on AI-generated code with additional implementation.


Quickstart
--------------------------------------------------------------------------------

```bash
mkdir -p /tmp/out
docker run --rm \
-v /tmp/out:/var/output \
-e USERGEN__COUNT=10000 \
ghcr.io/yo1000/dummy-user-generator:latest

ls -l /tmp/out
less /tmp/out/users.csv
```


Build and Run
--------------------------------------------------------------------------------

```bash
# Build
cargo build --release

# Run
./target/release/usergen --count 10000
```


Docker build and Run
--------------------------------------------------------------------------------

```bash
# Build
cargo build --release
docker build --tag dummy-user-generator \
--build-arg BIN=./target/release/usergen \
--build-arg DATA_DIR=./data .

# Run
mkdir -p /tmp/out
docker run --rm \
-v /tmp/out:/var/output \
-e USERGEN__COUNT=10000 \
dummy-user-generator
```
