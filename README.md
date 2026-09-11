# Firefox Custom Extension Icons

Customize and unify your Firefox toolbar extension icons using custom SVGs and `userChrome.css`.

Includes presets for:
- **Bitwarden**
- **uBlock Origin**
- **Firefox Multi-Account Containers**
- **1Password**

---

## Setup Instructions

### 1. Enable Custom Stylesheets in Firefox
1. In Firefox, navigate to `about:config`.
2. Accept the warning prompt.
3. Search for:
   ```text
   toolkit.legacyUserProfileCustomizations.stylesheets
   ```
4. Toggle it to **`true`**.

### 2. Locate Your Profile Folder
1. Navigate to `about:support`.
2. Find the **Profile Directory** (or **Profile Folder**) row and click **Open Directory** / **Show in Finder**.
3. Create a folder named `chrome` if it doesn't already exist.

### 3. Copy Files
Copy `userChrome.css` and the `icons/` folder into your `chrome/` folder:

```text
<firefox-profile>/
└── chrome/
    ├── icons/
    │   ├── 1password.svg
    │   ├── bitwarden.svg
    │   ├── firefox-containers.svg
    │   └── ublock.svg
    └── userChrome.css
```

### 4. Restart Firefox
Restart Firefox to apply your new icons.

---

## Adding More Icons

1. **Find the Extension ID**:
   - Go to `about:debugging#/runtime/this-firefox` (or check the *Add-ons* section in `about:support`).
   - Look for the extension's **Extension ID** (e.g., `uBlock0@raymondhill.net` or a UUID like `{446900e4-71c2-419f-a6a7-df9c091e268b}`).

2. **Add Your Icon**:
   - Place your SVG inside the `icons/` folder (e.g., `icons/my-extension.svg`).

3. **Update `userChrome.css`**:
   - Add a rule targeting the extension's ID:
   ```css
   :is(.webextension-browser-action, .eom-addon-button)[data-extensionid="YOUR_EXTENSION_ID"] .toolbarbutton-icon {
     list-style-image: url("icons/my-extension.svg");
   }
   ```
4. Restart Firefox.
