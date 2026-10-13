# Floorlink — Factory Network Atlas

An interactive factory-floor network mockup with six cabinets and 32 example devices, using the supplied cabinet photo as a visual reference.

## Run locally

With Node.js installed, run `npm start` from this directory and visit http://127.0.0.1:4173. No dependency installation or build step is required. Run `npm test` for layout and data validation tests.

## Use

- Click any map marker or panel card to open its cabinet front elevation.
- Click a device for its IP, model, description, status, location, and connections. Click a connected device to navigate to it, including across panels.
- Open the top-right IP directory, expand subnet groups, or search by IP, device, and panel. Selecting a result focuses the panel and opens the device inspector.
- Select **Edit panel** to drag devices from the library onto a rail or reposition existing equipment. Devices snap to the nearest available slot and cannot overlap or extend beyond a rail. Click a library item to add without dragging; **Move rail** provides a touch and keyboard alternative for repositioning.
- Edit device details and select connections in the inspector. IPv4 addresses must be valid and unique.
- Changes persist automatically in the current browser. Export a JSON backup and import it on another device. Import validates panel geometry, IP uniqueness, equipment placement, and connection references. Undo restores the latest edits for the current session.
- Drag the map to pan; scroll or use the controls to zoom. Escape closes the device form, inspector, or panel. Reduced-motion preferences are honored.

## Host anywhere

Deploy the contents of `dist/` to any static HTTPS host. There is no server API, database, runtime framework, or build requirement. Google Fonts is optional; system fonts provide fallbacks when unavailable. `server.mjs` is only a local preview server.

This prototype uses browser-local storage, not shared multi-user storage. Network status, devices, wiring, equipment displays, floor geometry, and IP addresses are fictitious demonstration data. The app does not scan networks, query real device statuses, or control equipment. The example addresses match the requested 172.168.0.xxx through 172.168.4.xxx ranges. Use your assigned addresses for real installations.

Source files: `dist/model.js` contains example data and validation; `dist/app.js` contains interactions and rendering; `dist/styles.css` contains styling and responsive layouts.
