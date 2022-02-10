## npm cli bug reproduction

When running `npm update` in this repo, it fails with the following message:

```
npm WARN tarball tarball data for escape-string-regexp@file:vendor/matcher-5.0.0.tar.gz (null) seems to be corrupted. Trying again.
npm WARN tarball tarball data for escape-string-regexp@file:vendor/matcher-5.0.0.tar.gz (null) seems to be corrupted. Trying again.
npm ERR! code ENOENT
npm ERR! syscall open
npm ERR! path <redacted-path>/npm-update-bug-repro/vendor/vendor/matcher-5.0.0.tar.gz
npm ERR! errno -2
npm ERR! enoent ENOENT: no such file or directory, open '<redacted-path>/npm-update-bug-repro/vendor/vendor/matcher-5.0.0.tar.gz'
npm ERR! enoent This is related to npm not being able to find a file.
npm ERR! enoent

npm ERR! A complete log of this run can be found in:
npm ERR!     /<redacted-path>/.npm/_logs/2022-02-10T09_35_25_467Z-debug-0.log
```

The interesting part is `vendor/vendor` in the path, indicating some error in the path resolution of npm update.
