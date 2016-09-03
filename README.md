# mkshadow

## generate SHA512 salted hashes

All I wanted to do was make some hashes I could use in some [Salt](http://www.saltstack.com) states.

After following a [lot](http://blog.loftninjas.org/2009/12/07/scripting-the-root-password-on-ubuntu-910-karmic/) of [outdated](http://www.linuxquestions.org/questions/linux-general-1/what-is-used-to-create-the-shadow-password-hash-602739/) or [distribution-specific](http://ubuntuforums.org/showthread.php?t=1169551) things, I found a [short python wrapper](http://alotofbytes.blogspot.com/2011/01/how-to-generate-encrypted-shadow.html) around the [crypt()](http://linux.die.net/man/3/crypt) system call.

But it still wasn't easy enough!

That's why I whipped this up.

## Usage

```
~$ mkshadow <enter>
Suitable password: <type something, not echoed back>
$6$w4hXGP54wp64$X6qFTFIT8omSS5vX6DYmEqiitD8TJQkO16IVjS09GVhyFiEwqawAqIkNMCwFZb3ylJTJpufDK2kGZXE99LIJ.0
```

Copy and paste the hash and put it wherever you need it.

## Security

* this doesn't ask you to confirm the password, so type carefully.
* I designed my salt generating method from [here](https://stackoverflow.com/a/10445962)

## Additional notes

* The `mkpasswd` and `chpasswd` binaries referenced in the earlier articles all exist in Fedora, but are either missing required functionality, or otherwise unsuitable.
* `openssl passwd` still doesn't have anything better than sha1 support. :(
* No additional packages should need to be installed on a modern Fedora desktop for this to work.
