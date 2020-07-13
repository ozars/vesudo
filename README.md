# vesudo

This is my workaround for running sudo in a virtual environment.

## Quick Install

```
wget https://raw.githubusercontent.com/ozars/vesudo/master/vesudo -O ~/.local/bin/vesudo
chmod +x ~/.local/bin/vesudo
```

## Example Usage

Below example is ran with Python 3.8.4rc1, virtualenv 20.0.26 and bash 5.0.16 on Debian Bullseye.

```console
~/tmp$ source .venv/bin/activate
(.venv) ~/tmp$ which python
/home/omer/tmp/.venv/bin/python
(.venv) ~/tmp$ vesudo which python
/home/omer/tmp/.venv/bin/python
(.venv) ~/tmp$ which pip
/home/omer/tmp/.venv/bin/pip
(.venv) ~/tmp$ vesudo which pip
/home/omer/tmp/.venv/bin/pip
(.venv) ~/tmp$ vesudo python -c 'import sys; print(sys.argv)' it works 'with spaced arguments' as well
['-c', 'it', 'works', 'with spaced arguments', 'as', 'well']
(.venv) ~/tmp$ vesudo echo '$HOME'
/root
```

## Known Issues

It doesn't work with bash syntax (`for`, `if` etc.) for some reason. Suggestions are welcome.

```console
(.venv) ~/tmp$ vesudo for i in 1 2 3 4\; do echo $i\; done
bash: line 2: for: command not found
```

## License

[The Unlicense](./LICENSE)
