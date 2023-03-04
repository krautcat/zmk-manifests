# ZMK manifests of [krautcat](https://github.com/krautcat)'s keyboards

### Prerequisites

 * [repo](https://gerrit.googlesource.com/git-repo)

## How to start

Prepare source code.

```bash
mkdir zmk
cd zmk
repo init -u git@github.com:krautcat/zmk-manifests.git
repo sync -j$(($(nproc) * 2))
```

Prepare keymaps.

```bash
cd krautcat-keymaps
./setup.sh
```

Prepare Zephyr's source code.

```bash
cd zmk
west init -l app/
west update
west zephyr-export
cd app/
```


Now you're ready to build my keymaps.

 - TK44
    
   ```bash
   west build -p -d build/tk44 -b tk44 -- \
       -DZMK_CONFIG="$(realpath ../../zmk-config/ladniy_customs/tk44/config)"
   ```

