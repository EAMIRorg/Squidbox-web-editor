# SquidBox Web Editor

React + TypeScript + Vite app for configuring and playing the SquidBox hardware over the Arduino Cloud Agent.

## Run Locally

```bash
# install
npm install
# start dev server (default http://localhost:5173/)
npm run dev
# lint (optional)
npm run lint
# build + preview (optional)
npm run build && npm run preview
```

## Connect to SquidBox from the Browser

1) Install the Arduino Cloud Agent: https://cloud.arduino.cc/download-agent/
2) Add localhost origins to the agent config:
   - macOS: `$HOME/Library/Application Support/ArduinoCreateAgent/config.ini`
   - Linux: `$XDG_CONFIG_HOME/ArduinoCreateAgent/config.ini` or `$HOME/.config/ArduinoCreateAgent/config.ini`
   - Windows: `%AppData%\ArduinoCreateAgent\config.ini`

   Replace contents with:
   ```
   gc = std
   hostname = unknown-hostname
   regex = usb|acm|com
   v = true
   appName = CreateAgent/Stable
   updateUrl = https://downloads.arduino.cc/
   origins = http://localhost:8000, https://localhost:8000, http://localhost:5173, https://localhost:5173, http://localhost:4173, https://localhost:4173, https://felixngfender.github.io/, https://eamirorg.github.io/squidbox-web-editor/
   crashreport = true
   autostartMacOS = true
   ```
3) Restart the Arduino Cloud Agent so the changes apply.
4) Plug in the SquidBox via USB.
5) Open the app (`npm run dev`) and reload until the port shows under “Connected Devices.” If prompted by Chrome, allow serial access.

If the agent isn’t trusted yet, visit `https://localhost:8991/info` once to allow the local certificate, then reload the app.
