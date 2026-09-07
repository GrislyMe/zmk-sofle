# ZMK Config - Sofle Keyboard

> **Fork Notice**
> This repository was forked from the upstream source in **March 2026** (update to your actual fork date) for custom Sofle keymaps, layout adjustments, and automated firmware builds.

Custom ZMK firmware configuration for the **Sofle** wireless split keyboard.

---

## Keymap Editing and Firmware Building

### 1. Using Keymap Editor (Recommended)
It is recommended to use the [Keymap Editor](https://nickcoutsos.github.io/keymap-editor/) web interface to customize keymaps:
* **Visual Interface**: Easily modify layers, keycodes, and macros through an intuitive UI.
* **GitHub CI/CD Integration**: Once linked to this repository, saving changes on the website automatically commits the updates and triggers a GitHub Actions build to compile your firmware.

### 2. Manual Configuration
* You can also directly edit the configuration files under the `config/` directory (e.g., `config/sofle.keymap` or `config/sofle.conf`).
* Commit and push your changes to the `main` branch to trigger an automatic GitHub Actions build.

---

## Retrieving Firmware (GitHub Actions)

1. After pushing changes to GitHub, navigate to the **Actions** tab in this repository.
2. Select the latest workflow run.
3. Scroll down to the Artifacts section to download the compiled `.uf2` / `.bin` firmware files.

---

## Flashing Instructions

1. Double-press the reset button on your target keyboard half (or dongle) to enter **Bootloader Mode**.
2. Connect the half to your computer using a USB cable. It will mount as a removable drive (e.g., `NICENANO`).
3. Drag and drop (or copy) the corresponding `.uf2` file into the mounted drive:
   * `sofle_left.uf2` / `sofle_left_nice_view.uf2` -> Left half
   * `sofle_right.uf2` / `sofle_right_nice_view.uf2` -> Right half
4. The drive will automatically unmount and reboot once flashing is complete.

> **Troubleshooting / Reset:**
> If Bluetooth pairing issues occur or the two halves fail to communicate, flash `settings_reset.uf2` to both halves first before re-flashing the main firmware.

---

## Local Development (Optional)

If you prefer building locally using `west` or Docker/Podman:

```bash
# Clone the repository
git clone [https://github.com/GrislyMe/zmk-sofle.git](https://github.com/GrislyMe/zmk-sofle.git)
cd zmk-sofle

# Initialize West workspace
west init -l config
west update

# Build firmware
west build -s zmk/app -b sofle_left -- -DZMK_CONFIG="$PWD/config"
```
![SofleKeyMap](keymap-drawer/eyelash_sofle.svg)
