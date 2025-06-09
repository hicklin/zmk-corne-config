# ZMK config files for a dvorak corne keyboard

This is a ZMK configuration used for a corne keyboard using a dvorak layout running on nice!nano v2.

## Building via github

1. Push any changes to the Github repository.
2. Go to the actions tab in the repository's page.
3. Click the latest workflow run.
4. Download the firmware in the Artifacts section.

## Building locally

Steps 1 to 3 only need to me done once.

1. Install the Zephyr SDK by following [this guide](https://docs.zephyrproject.org/latest/develop/getting_started/index.html)
up to and including the "Install Zephyr SDK" section.
2. If this repository is already cloned locally, run `west init -l <path to the config/west.yaml>`. This will pull in all the dependency modules alongside this project. If this repository is not yet cloned locally, run `west init -m <this repo's gitdub url>`. This will clone this repo together with all its dependencies.
3. Now run `west update` from the project root.
4. Build using `west build -s zmk/app -b "nice_nano_v2" --pristine -- -DZMK_CONFIG="/home/whicklin/Documents/openRepos/zmk-corne-config/config" -DKEYMAP_FILE="/home/whicklin/Documents/openRepos/zmk-corne-config/config/corne.keymap" -DSHIELD="corne_left nice_view_adapter nice_view"`. Note, this builds for the left shield. To build for the right, change `corne_left` to `corne_right` in `-DSHIELD`.
5. The firmware is located at `build/zephyr/zmk.uf2`.
6. Boot the nice!nano into the bootloader mode by double-clicking the reset button. This will make it appear like a mass-storage device.
7. Copy the firmware to the nice!nano.
