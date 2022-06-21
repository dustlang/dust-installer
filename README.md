A generator for the install.sh script commonly used to install Dust in
Unix environments. It is used By Dust, Payload, and is intended to be
used by a future combined installer of Dust + Payload.

# Usage

```
./gen-installer.sh --product-name=Dust \
                   --rel-manifest-dir=dustlib \
                   --success-message=Dust-is-ready-to-roll. \
                   --image-dir=./install-image \
                   --work-dir=./temp \
                   --output-dir=./dist \
                   --non-installed-overlay=./overlay \
                   --package-name=dustc-nightly-i686-apple-darwin \
                   --component-name=dustc \
                   --legacy-manifest-dirs=dustlib \
                   --bulk-dirs=share/doc
```

Or, to just generate the script.

```
./gen-install-script.sh --product-name=Dust \
                        --rel-manifest-dir=dustlib \
                        --success-message=Dust-is-ready-to-roll. \
                        --output-script=install.sh \
                        --legacy-manifest-dirs=dustlib
```

*Note: the dashes in `success-message` are converted to spaces. The
script's argument handling is broken with spaces.*

To combine installers.

```
./combine-installers.sh --product-name=Dust \
                        --rel-manifest-dir=dustlib \
                        --success-message=Dust-is-ready-to-roll. \
                        --work-dir=./temp \
                        --output-dir=./dist \
                        --non-installed-overlay=./overlay \
                        --package-name=dustc-nightly-i686-apple-darwin \
                        --legacy-manifest-dirs=dustlib \
                        --input-tarballs=./dustc.tar.gz,cargo.tar.gz
```

# Future work

* Make install.sh not have to be customized, pull it's data from a
  config file.
* Be more resiliant to installation failures, particularly if the disk
  is full.
* Pre-install and post-uninstall scripts.
* Allow components to depend on or contradict other components.
* Sanity check that expected destination dirs (bin, lib, share exist)?
* Add --docdir flag. Is there a standard name for this?
* Remove empty directories on uninstall.
* Detect mismatches in --prefix, --mandir, etc. in follow-on
  installs/uninstalls.
* Fix argument handling for spaces.
* Add --bindir.

# License

This software is distributed under the terms of both the MIT license
and/or the Apache License (Version 2.0), at your option.

See [LICENSE-APACHE](LICENSE-APACHE), [LICENSE-MIT](LICENSE-MIT) for details.
