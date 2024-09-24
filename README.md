# priv_keys-template

# Usage

```bash
croot && git clone -b 14 https://github.com/Huexxx/vendor_priv_keys-template vendor/priv/keys
```

```bash
cd vendor/priv/keys
```

```
./keys.sh
```

# Testing

Included `check_keys.py` script checks whether all apk/apex/capex files in the build out are signed with keys within its directory. Be aware that some targets are **expected** to be signed with vendor key, for example `com.android.apex.cts.shim.v1_prebuilt`.

```
$ ./check_keys.py ~/ROOT_DIR/out/target/product/DEVICE
/home/USER/ROOT_DIR/out/target/product/DEVICE/obj/ETC/com.android.apex.cts.shim.v1_prebuilt_intermediates/com.android.apex.cts.shim.apex is signed with an unknown key!
```

# Building

Add inherit on your vendor:

```makefile
$(call inherit-product-if-exists, vendor/priv/keys/keys.mk)
```
