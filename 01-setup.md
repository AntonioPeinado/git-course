# Set up

## Install

First of all lets install the `git client`:

* Windows: download the installer from [here](https://git-scm.com/download/win).
* Linux / Mac:

    ```bash
        sudo apt install git-all
    ```

Once done open a terminal and check everything is working:

```bash
git --version
```

## Hi, my name is Foo

Git need to know who you are, that information will be used to identify yout commits and to give you access to private repositories

```bash
git config --global user.name "Foo Bar"
git config --global user.email "foo@bar.baz"
```

To see your current settings you can use:

```bash
git config --list
```

If using the `--global` flag that configuration will be used in all of your projects, if you want to override it just execute the above commands, ommiting that flag, inside your project directory.

## Sometimes, we will need to write

For the occasions in which `git` needs access to a `text editor` we can configure it to use one, otherwise it will use our default one, if any.

```bash
git config --global core.editor (alias || "path/to/executable")
```