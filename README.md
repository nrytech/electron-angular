# How create a desktop app with Angular and Electron
Angular is one of the most popular Javascript framework to create web application.
But it can be also used to generate Desktop application. <br/>
On this project we will mix [Angular](https://angular.dev/) with [Electron](https://www.electronjs.org/) 
to build an application that can be used as a web application but also as a desktop application.

## Setup angular:
```
// Generate the angular app with ng (@angular/cli)
ng electron-angular
cd electron-angular
```

## Setup Electron:
[ElectronJS](https://www.electronjs.org/)  Electron embeds Chromium and Node.js to enable web developers to create desktop applications.<br/>
It is cross-platform compatible with macOS, Windows, and Linux, Electron apps run on three platforms across all supported architectures.<br/>
Electron is an open source project maintained by the OpenJS Foundation and an active community of contributors.<br/>
```
npm install -D electron
```

After this stage you have to create the entry point of the electron app [electron-main.js](electron-main.js).
Don't forget to add the property `main`  on your [package.json](package.json) to this entrypoint.

## Setup Electron Forge:
[Electron Forge](https://electronforge.io/) is an all-in-one tool for packaging and distributing Electron applications. 
It combines many single-purpose packages to create a full build pipeline that works out of the box, 
complete with code signing, installers, and artifact publishing. 
For advanced workflows, custom build logic can be added in the Forge lifecycle through its Plugin API. 
Custom build and storage targets can be handled by creating your own Makers and Publishers.
```
// Install dependency
npm install -D @electron-forge/cli
// Let the electron-forge setup is dependency
npx electron-forge import
```
### Setup Electron Forge Make:
The electron-forge command make will generate executable file. To configure it update the [forge.config.js](forge.config.js) configuration file. 

## Personalisation:
I remap the standard electron-forge command start, package, make into electron:{cmd} for more clarity.

## How Use:

### Run web app:
```
npm start
```

### Run app as desktop app: 
```
npm run electron:start
```

### Generate desktop executable file:
The following command will generate executable file on [./release/make](release%2Fmake).
With electron-forge you can generate executables for multiple OS (macOS, windows, linux). 
The setup of this generation wil be done on the [forge.config.js](forge.config.js) configuration file.<br/>
See [official documentation](https://www.electronforge.io/config/makers) do learn more 
```
npm run electron:make
```