## What does this do?
This [Automatic1111](https://github.com/AUTOMATIC1111/stable-diffusion-webui) extension adds a configurable dropdown to allow you to change settings in the txt2img and img2img tabs of the Web UI.

This allows you to do things like swap from low quality rendering settings to high quality. Or apply hires settings that uses your favorite anime upscaler. Or set image dimensions to make a wallpaper. You can even use it to set custom script fields like XYZ plot values or ControlNet values.

Works with [stable-diffusion-webui-forge](https://github.com/lllyasviel/stable-diffusion-webui-forge). Untested with [SD.Next](https://github.com/vladmandic/automatic)

## Screenshots
The new dropdown in the image gallery.

![gallery](https://i.imgur.com/f6PpXud.jpeg)

Dropdown values (configurable), select one and the generation settings values will be applied to the Web UI.

![dropdown](https://i.imgur.com/GsywR4x.jpeg)

Clicking the add/remove [🖌️] button lets you create and delete custom presets of settings currently in the Web UI. Custom fields added by other scripts/extensions can also be used by clicking the [📂 Add custom fields...] button. Each button has tooltips to help you.

![addremove](https://i.imgur.com/iQZpGEe.jpeg)

Screenshot of config-txt2img.json, which can be opened with the open config file [📂] button. You can use this if you want manual control while editing your presets. If you decide to edit the config this way, you can use the refresh [🔄] button. config-img2img.json also exists for the img2img tab.

![config](https://i.imgur.com/oUyMBq9.jpeg)

## Installation
#### Easy way
* In your Automatic1111 Web UI, go to the Extensions tab > Install from URL > URL for extension's git repository: `https://github.com/Zyin055/Config-Presets`
* Click the Install button
#### Manually
* `git clone` this repo to the `extensions` folder in your Web UI installation

## Known issues
* Unable to save fields in the quick access area at the top of the page (checkpoint, vae, clip skip, etc)
* Unable to save multi-select fields, such as the XYZ script's checkpoint name and sampler fields

## Changelog
<details>
    <summary>Click to view Changelog</summary>
    
#### 10/18/2024
* Added a new argument which an be put in webui-user.bat in COMMANDLINE_ARGS: `--configpresets-dir` to point to a different folder with Config Presets configuration files instead of using this extension's folder. Useful if you have multiple installations of A1111 and want to share your custom settings between them.
    * Example: in webui-user.bat: `set COMMANDLINE_ARGS= --configpresets-dir "C:\path\to\Config Presets config files"`
#### 8/15/2024
* Support for Forge's Distilled CFG (txt2img_distilled_cfg_scale) for Flux models
* Added new presets for Flux Dev/Schnell, tweaked existing presets
#### 4/14/2024
* Fixed backwards compatibility issue introduced in yesterdays update.
#### 4/13/2024
* Updated for Automatic1111 [v1.9.0](https://github.com/AUTOMATIC1111/stable-diffusion-webui/releases/tag/v1.9.0)
* There is a new "Schedule type" dropdown next to the "Sampling method" dropdown which splits off the scheduler from the sampler. This means that all of your config presets that have a saved sampler needs to be renamed/fixed to remove the scheduler text at the end. For example, if you have `txt2img_sampling` set to "DPM++ 2M Karras", it now needs to be set to "DPM++ 2M" with the new `txt2img_scheduler` dropdown set to "Karras". You can do this by manually editing your `config-txt2img.txt` and `config-img2img.txt` files at `/extensions/Config-Presets`, or by deleting the bad presets in the web UI and remaking them.
#### 4/02/2024
* Improved error handling when the config files are edited manually
#### 3/28/2024
* Made the buttons smaller, fixes cosmetic alignment issue
* Added a refresh button to reload the config file from disk, useful if you edit the config text file manually
* Updated default config presets
#### 2/05/2024
* Fixed an error when saving the hires fix sampler dropdown field (hr_sampler) and selecting the value "Use same sampler"
#### 11/18/2023
* Fixed an issue when saving a dropdown field in Web UI versions before 1.6.0
#### 9/16/2023
* Added a Reapply button
#### 9/04/2023
* Fixed config presets that used radio button components not working
#### 8/31/2023
* Updated for Automatic1111 [v1.6.0](https://github.com/AUTOMATIC1111/stable-diffusion-webui/releases/tag/v1.6.0)
* Added support for "Refiner" (txt2img_enable-checkbox) and "Switch at" (txt2img_switch_at) components for txt2img and img2img, which are used for SDXL Refiner models. The refiner checkpoint component is not supported.
#### 5/15/2023
* The UI no longer needs to be reloaded when creating a new config preset
#### 4/29/2023
* Updated for the March 29th Automatic1111 version which uses Gradio 3.23
* Added the ability to add almost any field on the UI to a config preset with the "Add tracked fields..." button
#### 3/06/2023
* Added the ability to select which fields are saved when creating a new config preset (before, this could have been done manually by editing the .json config file)
* Moved some buttons around in the UI for creating a new config preset
* Added Hires Upscaler (txt2img_hr_upscaler), Upscale by (txt2img_hr_scale), and Restore Faces (txt2img_restore_faces) as eligible fields to be used in a config preset
* Tweaked default config preset values created during installation
* Removed "Default" preset since it doesn't work with new system that lets you ignore fields
#### 2/10/2023
* Manually removing a preset value in the config file will make that value be ignored
#### 2/09/2023
* Added 768x768, 1080p, 1440p, and 4k presets for txt2img (they won't show up for existing installations, you'd need to delete your config-txt2img.json file to have it recreated with the new presets)
#### 1/02/2023
* Your custom presets will be wiped, you will need to remake any saved custom presets because of changes made in Automatic1111
* The Config Presets dropdown in the txt2img and img2img tabs now use separate config files and thus have separate presets
* Saving a new preset now requires a Web UI restart (done automatically)
* Added support for the Sampler method turning from a checkbox into a dropdown
* Added support for the removal of Firstpass width/height being replaced by Upscale by
#### 12/21/2022
* Added the "Add/Remove..." button to create and delete config presets within the Web UI
#### 12/19/2022
* config.json will be created on first startup, user edits will not be overwritten when updating the extension after updating to this version
#### 12/15/2022
* Fix for installation error on linux
#### 12/13/2022
* config.json was tweaked, added Firstpass width and Firstpass height
* Better support for img2img tab compatibility
#### 12/12/2022
* Initial Release
</details>
