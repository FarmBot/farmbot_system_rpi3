# Maintaining This Repo

```bash
git clone git@github.com:Farmbot-Labs/nerves_system_farmbot_rpi3.git
cd nerves_system_farmbot_rpi3
git remote add upstream git@github.com:Nerves-Project/nerves_system_rpi3.git
git fetch --all
git merge v<new upstream release>
git push origin master
cd ..
git clone git@github.com:Nerves-Project/nerves_system_br -b v<latest release>
./nerves_system_br/create-build.sh ./nerves_system_farmbot_rpi3/nerves_defconfig BUILD_RPI3
cd BUILD_RPI3
make system # this will take a while.
# create github release.
# upload system artifact.
cd nerves_system_farmbot_rpi3
mix hex.publish package
```
