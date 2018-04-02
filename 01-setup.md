# Setup

## Install

First of all lets install the `Git client`:

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

For the occasions in which `Git` needs access to a `text editor` we can configure it to use one, otherwise it will use our default one, if any.

```bash
git config --global core.editor (alias || "path/to/executable")
```

## Going pro

We can configure an `SSH` key so we don't need to care about our username or password, and in some situations this will be needed for installing dependencies from a private repository, for example if using `NPM`.

### Generating an SSH key

First thing we need is creating an `SSH` key:

1. Open a shell (__if running Windows use `Git bash`__)
2. Enter the following command to create a new key:

    ```bash
       ssh-keygen -t rsa -b 4096 -C "foo@baz.bar"
    ```
3. Once promted to do so, enter the location in which to store the key, or press `enter` for using the `default` location.
4. Now you can opt to enter a password for using the key or not, if not leave the next promp blak and press `enter`. If you decide to use one note that you will be asked for it every time.

### Add your SSH key to the ssh-agent

`ssh-agent` is in charge of managing your SSH keys. First of all start it in the background:

```bash
eval "$(ssh-agent -s)"
```

Then add the key:

```bash
ssh-add ~/.ssh/id_rsa # this is the default path to your private key
```

### Add your SSH key to your Git server account

Last step is to add your __`public`__ key to your Git server account, we will be using `Github` for illustration purposes.

1. Copy the __`public`__ key by opening the __`.pub`__ file that was generated in the first section by copying the full output of the next command:

    ```bash
    cat ~/.ssh/id_rsa.pub
    ```
2. Click on your profile picture and go to `settings`.
3. In the left menu navigate to `SSH and GPG keys`.
4. Click on `new SSH key`.
5. Insert a name that represents your current computer, since the key you previously generated is specific to it, for example `Office computer`.
6. Paste your previously coppied key and click on `Add SSH key`.

### Verify it works

Finally lets check everyting is setup correctly by running:

```bash
ssh -T git@github.com # or whichever server you are using
```

Dont worry abot the message saying the autenticity can't be established, this is just because is the first time we connect to that host, type `yes` and press `enter`, you should see a greetings message.

## Sources

* [Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* [First time Git setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)
* [Connecting to GitHub with SSH](https://help.github.com/articles/connecting-to-github-with-ssh/)