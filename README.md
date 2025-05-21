## Install or update Python on macOS


1. Install Homebrew (Package Manager for macOS as well as Linux) if you have not already.

```
/bin/bash -c "$(curl -fsSL 
https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. Next install `pyenv` (Python version manager).

```
brew install pyenv
```

3. Next, upgrade `pyenv` (if need be) to capture newer python versions.

```
brew upgrade pyenv
```

4. List all available Python versions and pick out the required version of your choosing.

```
pyenv install -l
```

>[!TIP]
> This is a more helpful version of the above. It lists out only the release versions of the specified Python version i.e. `3.13.*`
```
pylist() {
  pyenv install -l | grep '^[ ]*'${1}'.*[0-9]$'
}
```

5. Insert the above into `~/.bashrc`, `~/.zshrc` (default shell on macOS since Catalina in 2019), or simply paste it in Terminal window and run `pylist <python version>`.

6. Install the desired version e.g. 3.13.0, or use :latest for the latest release version.

```
pyenv install 3.13:latest
```

7. Next, you want to edit the `.zshrc` shell config file.
```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init --path)"\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
```

8. Save the file and source it.

```
source ~/.zshrc
```

8. You may set the latest version of Python as global default.

```
pyenv global 3.13.x
```

9. Verify the change by running `python --version`. You should see the version of Python you set as the global default.
