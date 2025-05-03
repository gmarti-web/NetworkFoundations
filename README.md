# Network Foundations: PTW330 portfolio project

This project hosts the Network Foundations team's PTW330 portfolio project.

This project uses [Jekyll][1] and [Vale][2]. Jekyll renders all Markdown documents into static blog pages. This controls how the documents look to viewers in their browser. Vale lints these documents to keep them error-free. It checks for spelling issues, grammatical errors, over-complicated content, and more. Together, they convert the plain text documents in this repository into a vibrant, well-structured site.

The rest of this README page describes how to build and add changes to this project on your local computer.

## How to build this project locally

Build the site on your local computer to see how Jekyll renders your document. Lint, or check, your document for grammatical or spelling errors before you commit it.

### Install dependencies

Follow the instructions for your operating system to install Jekyll and [Bundler][3].

<details>
<summary>Linux, Ubuntu, or Debian</summary>

1. Install Ruby and prerequisites:

    ```console
    sudo apt-get install ruby-full build-essential zlib1g-dev
    ```

1. Add a gem installation directory for your user account to your `~/.bashrc` file.

    ```console
    echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
    echo 'export PATH="$PATH:$HOME/gems/bin"' >> ~/.bashrc
    source ~/.bashrc
    ```

1. Install Jekyll and Bundler.

    ```console
    gem install jekyll bundler
    ```

1. Run `jekyll -v` to check the installation.

To learn more about installing Jekyll on Ubuntu, see [Jekyll on Ubuntu][4].

</details>

<details>
<summary>macOS</summary>

1. Install [HomeBrew][5].

    ```console
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

1. Install `chruby` and the latest Ruby version.

    ```console
    brew install chruby ruby-install
    ```

    ```console
    ruby-install ruby 3.4.1
    ```

1. Configure your shell to use `chruby`.

    ```console
    echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.bash_profile
    echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.bash_profile
    echo "chruby ruby-3.4.1" >> ~/.bash_profile
    source ~/.bash_profile
    ```

1. Install Jekyll and Bundler.

    ```console
    gem install jekyll bundler
    ```

1. Run `jekyll -v` to check the installation.

To learn more about installing Jekyll on macOS, see [Jekyll on macOS][6].

</details>

<details>
<summary>Windows</summary>

Jekyll doesn't officially support Windows. You can, though, install Jekyll with the [RubyInstaller][14].

1. Download and install the recommended Ruby+Devkit version from [RubyInstaller downloads][15].

  * Use the default options.

1. Run the `ridk install` step from the installation wizard. From the options, choose `MSYS2 and MINGW development toolchain`.
1. Open a new terminal and install Jekyll and Bundler.

  ```console
  gem install jekyll bundler
  ```

1. Run `jekyll -v` to check the installation.

To learn more about installing Jekyll on Windows, see [Jekyll on Windows][16].

</details>

For a complete list of installation methods, see [Installing Ruby][7].

### Install gems from `Gemfile`

This project's `Gemfile` lists all the gems that this project needs. You only need to install these gems the first time you build the site.

To install the needed gems:

1. In your terminal, go to the project's root folder.

    ```console
    git clone https://github.com/gmarti-web/gmarti-web.github.io.git
    cd gmarti-web.github.io.git
    ```

2. Set the local gem folder.

    This keeps the gems you install for this project scoped to this folder.

    ```console
    bundle config path 'vendor/bundle' --local
    ```

3. Install the project's required gems from the `Gemfile`.

    ```console
    bundle install
    ```

This installs this project's gems to a local folder called `vendor/bundle`.

### Start the server

After you install the gems, use `bundle` to start the Jekyll server:

```console
bundle exec jekyll serve
```

To see the rendered site, go to [http://localhost:4000][8].

### Install Vale

This project uses Vale to check, or lint, for any writing errors.

To install Vale, use your operating system's package manager.

<details>
<summary>Linux, Ubuntu, or Debian</summary>

1. For Linux and Debian, you must install the [Snapcraft][9] daemon. For Ubuntu, which has the daemon pre-installed, skip to step two.

    1. For Linux, remove the `nosnap.pref` file from your native package manager's preference folder. For Debian, skip to step ii.

        ```console
        sudo mv /etc/apt/preferences.d/nosnap.pref ~/Documents/nosnap.bkp
        ```

    1. Update `apt`.

        ```console
        sudo apt update
        sudo apt upgrade -y
        ```

    1. Install `snapd`.

        ```console
        sudo apt install snapd
        ```

1. Install Vale.

    ```console
    snap install vale
    ```

1. Run `vale -v` to check the installation.

This installs Vale and adds it to your `$PATH` variable.

</details>

<details>
<summary>macOS</summary>

1. Install [HomeBrew][5].

    ```console
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

1. Install Vale.

    ```console
    brew install vale
    ```

1. Run `vale -v` to check the installation.

This installs Vale and adds it to your `$PATH` variable.

</details>

<details>
<summary>Windows</summary>

1. Install [Chocolatey][17].

    1. [Open a PowerShell terminal as an administrator][19]. To install as a non-admin, see Chocolatey's documentation on [non-administrative installation][18]
    1. Run `Get-ExecutionPolicy`.

        * If it returns `Restricted`, run `Set-ExecutionPolicy Bypass -Scope Process`.

    1. Install Chocolatey.

        ```powershell
        Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
        ```

    1. Run `choco` to check the installation.

1. Install Vale.

    ```console
    choco install vale
    ```

1. Run `vale -v` to check the installation.

This installs Vale and adds it to your `%PATH%` variable.

</details>

To learn more about installing Vale, see [Install–Vale CLI][10].

After you install Vale, install the packages listed in the `.vale.ini` file:

```console
vale sync
```

To lint a single file, run the following command:

```console
vale path/to/document.md
```

To lint all the files in a folder, run the following command:

```console
vale path/to/folder/
```

## How to contribute to this project

To contribute to the project:

1. [Find an issue][11] you want to work on. If one doesn't exist, [create one][12].
1. Check out the repository.
1. Create a new branch that describes your work.

    ```console
    git checkout -b my-branch
    ```

1. [Build the project on your local computer][13].
1. Make your changes, test them on your local server, and then lint for writing errors.
1. Push your changes to a new remote branch.
1. Create a new pull request.

The code owner reviews the pull request. If approved, they'll merge the changes into the main branch. If not, they'll add their feedback to the pull request.

[1]: https://jekyllrb.com/
[2]: https://vale.sh/
[3]: https://bundler.io/
[4]: https://jekyllrb.com/docs/installation/ubuntu/
[5]: http://brew.sh/
[6]: https://jekyllrb.com/docs/installation/macos/
[7]: https://www.ruby-lang.org/en/documentation/installation/ 
[8]: http://localhost:4000
[9]: https://snapcraft.io/
[10]: https://vale.sh/docs/install
[11]: https://github.com/gmarti-web/gmarti-web.github.io/issues
[12]: https://github.com/gmarti-web/gmarti-web.github.io/issues/new?template=feature-request.yml
[13]: #how-to-build-this-project-locally
[14]: https://rubyinstaller.org/
[15]: https://rubyinstaller.org/downloads/
[16]: https://jekyllrb.com/docs/installation/windows/
[17]: https://chocolatey.org/install
[18]: https://docs.chocolatey.org/en-us/choco/setup#non-administrative-install
[19]: https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/starting-windows-powershell?view=powershell-7.5#run-with-administrative-privileges
