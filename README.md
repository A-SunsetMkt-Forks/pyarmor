# Pyarmor

Pyarmor is a command line tool used to import or run obfuscated python
scripts. Only by a few extra files, pyarmor can run and imported
obfuscated files as normal python scripts.

Pyarmor just likes an enhancement which let python could run or import
obfuscated files.

## Main Features

- Run obfuscated script or import obfuscated module
- Expire obfuscated files
- Bind obfuscated files to harddisk, mac address, ip address etc.

## Obfuscation Mechanism

Pyarmor obfuscates python scripts by 2 ways:

* First obfuscate byte code of each code object

* Then obfuscate whole code object of python script

More information refer to [How to obfuscate python scripts](src/mechanism.md)

## Support Platforms

- Python 2.5, 2.6, 2.7 and Python3

- Prebuilt Platform: win32, win_amd64, linux_i386, linux_x86_64, macosx_intel

- Embeded Platform: Raspberry Pi, Banana Pi, ts-4600

The core of [Pyarmor] is written by C, the only dependency is libc. So
it's not difficult to build for any other platform, even for embeded
system. Contact <jondy.zhao@gmail.com> if you'd like to run encrypted
scripts in other platform.

The latest platform-depentent library could be
found [here](http://pyarmor.dashingsoft.com/downloads/platforms)

## Quick Start

### Installation

Got source package from [pypi/pyarmor](https://pypi.python.org/pypi/pyarmor)

Pyarmor is a command line tool, main script is pyarmor.py. After you
got source package, unpack it to any path, then run paramor.py as
common python script

```
    python pyarmor.py
```

### Basic Usage

The following examples show how to obfuscate a python package
**pybench**, which locates in the **examples/pybench** in the source
of pyarmor.

Obfuscate package **pybench** first time

```
    python pyarmor.py obfuscate --src examples/pybench --entry pybench.py

    # This command will create 2 files in the path specified by --src:
    #
    #    .pyarmor_config, .pyarmor_capsule.zip
    #
    # And save all the obfuscated scripts to output path "dist" in the
    # current path
    #
    cd dist
    
    # Check obfuscated script
    cat pybench.py
    
    # Run obfuscated script
    python pybench.py
```

Once any script of package **pybench** changed, run the following
command to obfuscate those updated scripts

```
    python pyarmor.py obfuscate --src examples/pybench
```

Obfuscate package **pybench**, save all extra files to another path

```
    mkdir projects
    python pyarmor.py init --path projects/pybench \
                           --src examples/pybench --entry pybench.py
                           
    # All the extra files will be saved to --path
    cd projects/pybench
    
    # And there is a shell script "pyarmor" is created at the same time.
    # (In windows, the name is "pyarmor.bat")
    #
    # Now run "pyarmor" to obfuscated all the scripts by subcommand "build"
    #
    ./pyarmor build
    
    # Check obfuscated script
    cd dist
    cat pybench.py
    
    # Run obfuscated script
    python pybench.py
```

More usage, refer to [User Guide](src/user-guide.md)

## License

Pyarmor is published as shareware. Free trial version that never expires, the limitation is

- Project Capsule generated by trial version is NOT random, but FIXED by hardcode.

A registration code is required to generate random project capsule.

- Personal user: one registration code is enough.
- Company user: one registration code is only used for one project/product.

### Purchase

Click [Purchase](https://shopper.mycommerce.com/checkout/cart/add/55259-1),

A registration code will be sent to your immediately after payment is completed successfully.

After you receive the email which includes registration code, copy
registration code only (no newline), then replace the content of
"license.lic" with it.

### Check License

```
    python pyarmor.py --version
```

**The registration code is valid forever, it can be used permanently.**

## [Change Log](ChangeLog.rst)

## [Report issuses](https://github.com/dashingsoft/pyarmor/issues)

Any question feel free email to <jondy.zhao@gmail.com>
