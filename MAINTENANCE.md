# Maintaining This Repo

*replace all `<text in brackets>` with desired version strings*

```bash
apt update
apt upgrade -y
apt install -y build-essential automake autoconf git squashfs-tools ssh-askpass pkg-config curl libssl-dev libncurses-dev bc m4 unzip cmake python3 libwxgtk3.2-dev libnl-genl-3-dev bc rsync subversion libmnl-dev
wget https://github.com/fwup-home/fwup/releases/download/v1.10.2/fwup_1.10.2_amd64.deb
dpkg -i fwup_1.10.2_amd64.deb
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.14.0
echo -e '\n. $HOME/.asdf/asdf.sh' >> ~/.bashrc
source ~/.bashrc
asdf plugin-add erlang
asdf plugin-add elixir
asdf install erlang <erlang version>
asdf install elixir <elixir version>
asdf global erlang <erlang version>
asdf global elixir <elixir version>
git clone https://github.com/farmbot/farmbot_system_rpi3
cd farmbot_system_rpi3
# ------- begin updates -------
git remote add upstream https://github.com/nerves-project/nerves_system_rpi3
git fetch --all
git merge v<new upstream release>
# fix conflicts in text editor. (usually just `VERSION`)
git add .
git commit -am 'merge upstream'
git push origin main
# -------- end updates --------
mix archive.install hex nerves_bootstrap
mix deps.get
mix compile # this will take a while
mix nerves.artifact
# create github release and upload system artifact
```

## See also:
https://hexdocs.pm/nerves/installation.html

https://hexdocs.pm/nerves/customizing-systems.html
