# Work Time & Salary Tracker PWA

This folder contains an installable mobile PWA for tracking Warehouse and Courier shifts, estimating Gross/Net salary, recording fuel reimbursement, viewing work history, and exporting the current month to CSV.

## Key behavior

- Active shifts, settings, selected language, and history are stored locally on the device.
- The live timer is calculated from timestamps, so it resumes correctly after reopening the PWA.
- Fuel reimbursement is displayed separately and is not included in salary.
- The service worker caches the application shell after the first successful load, allowing normal use without a network connection.

## Install on iPhone

Publish the complete `pwa` folder, including `icons/`, to an HTTPS static host. Open its URL in Safari, tap **Share**, then choose **Add to Home Screen**. HTTPS is required for service-worker offline support on iPhone.

## Local preview

```powershell
& 'C:\Users\Artem\.cache\codex-runtimes\codex-primary-runtime\dependencies\python\python.exe' -m http.server 8765 --directory .\pwa
```

Then open `http://localhost:8765`.

## Updating the PWA

When application-shell files change, update the `CACHE` value in `sw.js`. The service worker installs the complete shell, removes older caches during activation, and immediately takes control of open pages.
