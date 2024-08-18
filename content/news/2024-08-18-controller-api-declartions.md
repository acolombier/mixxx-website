title: Controller API declarations for JavaScript mapping developers
authors: Jörg Wartenberg
tags: 2.4, controller
date: 2024-08-18 16:57:58


If the support of a DJ controller requires more than the semantic 1:1 mapping of MIDI codes, Mixxx offers the possibility to use freely programmable Javascript code to implement such more complex functionalities.

The Mixxx internal Application Programming Interface (API) for such controller scripts was previously only partially documented, in the [Mixxx Wiki](https://github.com/mixxxdj/mixxx/wiki/).

This has changed with Mixxx 2.4, now there are formal TypeScript declarations for each individual API class/method. These can be read by any code editor with [Language Server Protocol (LSP)](https://en.wikipedia.org/wiki/Language_Server_Protocol) support, to be visualized to the developer while typing his controller scripting code.
![Screenshot of documentation from controller API declaration visualized in editor]({static}/images/news/ControllerApiDocuInEditor.png)
Popular editors and IDEs with LSP support are Atom, Eclipse, Sublime Text, Visual Studio and Visual Studio Code.

In addition to the inline visualization of the documentation, the syntax is also checked against the TypeScript declarations. Usage errors are reported directly when writing the code in the editor.
![Screenshot of syntax check against controller API declaration visualized in editor]({static}/images/news/ControllerApiSyntaxCheckInEditor.png)

## How to use it?
Development of mappings and controller scripts is usually done in the subdirectory `controllers` of the [Mixxx Settings Directory](https://manual.mixxx.org/latest/chapters/appendix/settings_directory), while the common files (like `common-controller-scripts.js`) which comes with Mixxx, are store in the subdirectory `controllers` of Mixxx installation directory, or `./mixxx/res/controllers` if you built Mixxx yourself. This is also the location, where the TypeScript files with the declarations of the Mixxx controller API are stored. The LSP language server need to know the location of all of them. To tell the LSP server general settings and the locations of these files, you need to create a file with the name `jsconfig.json` placed next to your JavaScript controller script file, in the `controllers` directory in your `Mixxx Settings Directory`.

The `jsconfig.json` must have a content like this:

    {
    "compilerOptions": {
        "target": "es6",
        "checkJs": true,
        "lib": [ "ES2016" ]
    },
    "include": [
        "./filename_of_your_controller_script.js",
        "C:/Program Files/Mixxx/controllers/common-controller-scripts.js",
        "C:/Program Files/Mixxx/controllers/common-hid-packet-parser.js",
        "C:/Program Files/Mixxx/controllers/engine-api.d.ts",
        "C:/Program Files/Mixxx/controllers/color-mapper-api.d.ts",
        "C:/Program Files/Mixxx/controllers/console-api.d.ts",
        "C:/Program Files/Mixxx/controllers/hid-controller-api.d.ts"
    ]
    }

The content of the jsconfig.json:

* `The compilerOptions` section contains information about the JavaScript engine. Especially it overwrites the default included libraries, which only apply to JavaScript in webbrowsers
* The first file entry in the include section is the controller script under development, located next to the `jsconfig.json`
* `common-controller-scripts.js` is a JavaScript library used in most controller scripts, and is part of the Mixxx installation.
* `common-hid-packet-parser.js` is also JavaScript library but only for controllers using the HID protocol
* `engine-api.d.ts`, `color-mapper-api.d.ts` and `console-api.d.ts` are part of the Mixxx installation and contain TypeScript API declarations, which should be added for any controller script development
* `hid-controller-api.d.ts` is also such a declaration file, but specific to the communication protocol, because the APIs for HID and MIDI use the same symbols
    * For HID controllers use `hid-controller-api.d.ts`
    * For MIDI controllers use `midi-controller-api.d.ts`

The .js files listed in the include section of the `jsconfig.json` must exactly match the files in the `<scriptfiles>` section of the controller mappings .xml file. But, note that the .xml only contains the file names, while the `jsconfig.json` requires the full paths (relative to the position of the `jsconfig.json` file).

Once you have the `jsconfig.json` file in place, you only need to open the folder containing the file in your editor, and all listed files will be found and read by the LSP server.
