# electron-transparency-issue

This example demonstrates the chromium window transparency issues with electron.

- https://github.com/electron/electron/issues/2170
- https://bugs.chromium.org/p/chromium/issues/detail?id=854601

Transparency only works if I call `app.disableHardwareAcceleration()` and delay window creation
with `app.on('ready', () => setTimeout(createWindow, 100))`. If any of these is missing, the background is black and does not get updated, previously rendered frames are visible.

My problem with this hacky solution is that animations become janky without hardware acceleration enabled.

Tested:
- __OS__: Arch Linux
- __Compositor__: compton
- __Driver__: xf86-video-intel
- __Display server__: xorg-server

(all packages were updated to the latest stable version at June 20, 2018)

## Running the examples

You will need node.js (preferably latest LTS verison, I used `8.11.1`)

```
npm install
npm run start-works
npm run start-doesnotwork
```