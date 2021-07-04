# Debugging

## Debugging on the Command Line

If you're using Electron 1.8 or later, you can specify the `--inspect-electron` flag when running `electron-forge start`, which will set the [Electron `--inspect`flag](http://electronjs.org/docs/tutorial/debugging-main-process#--inspectport) with the default debugger port.

```bash
electron-forge start --inspect-electron
```

This will allow you to open `chrome://inspect` in Google Chrome and attach a debugger to the main process of your app.

## Debugging with VS Code

Debugging your Electron main process through VS Code is ridiculously easy with Forge. Simply add this as a launch config in VSCode and you're good to go.

{% hint style="info" %}
You need to be using Electron 1.8 or later for this launch config to work.

If you are using &lt; 1.8 you should really be updating Electron anyway.
{% endhint %}

{% code title="launch.json" %}
```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Debug Main Process",
      "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/electron-forge-vscode-nix",
      "windows": {
        "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/electron-forge-vscode-win.cmd"
      },
      "runtimeArgs": [],
      "cwd": "${workspaceFolder}",
      "timeout": 60000
    }
  ]
}
```
{% endcode %}

