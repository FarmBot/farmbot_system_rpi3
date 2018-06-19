# Maintaining This Repo

```bash
git clone git@github.com:Farmbot-Labs/nerves_system_farmbot_rpi3.git --recursive
cd nerves_system_farmbot_rpi3
git remote add origin git@github.com:Nerves-Project/nerves_system_rpi3.git
git fetch --all
git rebase -i v<new upstream release>
# fix conflicts in text editor. (usually just `VERSION`)
git rebase --continue
git push origin master --force
cd ..
git clone git@github.com:Nerves-Project/nerves_system_br -b v<latest release>
./nerves_system_br/create-build.sh ./nerves_system_farmbot_rpi3/nerves_defconfig RPI3
cd RPI3
make system # this will take a while.
# create github release.
# upload system artifact.
cd nerves_system_farmbot_rpi3
mix hex.publish package
```
