# Maintaining This Repo

```bash
git clone git@github.com:Farmbot/farmbot_system_rpi3.git
cd farmbot_system_rpi3
git remote add upstream git@github.com:Nerves-Project/nerves_system_rpi3.git
git fetch --all
git merge v<new upstream release>
git push origin main
cd ..
git clone git@github.com:Nerves-Project/nerves_system_br -b v<latest release>
./nerves_system_br/create-build.sh ./farmbot_system_rpi3/nerves_defconfig BUILD_RPI3
cd BUILD_RPI3
make system # this will take a while. dependencies may need to be installed/upgraded
cd ..
# create github release.
# upload system artifact.
cd farmbot_system_rpi3
mix hex.publish package
```
