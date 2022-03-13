# macOS

## File Extension Support

Extensions are defined via engines. Engines with macos support:

-   [rnv-engine-rn-macos](engines/engine-rnmacos.md) (default)
-   rnv-engine-rn-electron (support for macOS might be deprecated in the future)

## Run the app

```
rnv run -p macos
```

Clean and Re-build platform project

```
rnv run -p macos -r
```

## App Store Releases

`renative.json` scheme snippet for automatic signing releases

```json
{
    "platforms": {
        "macos": {
            "buildSchemes": {
                "appstore": {
                    "id": "YOUR_APP_ID",
                    "teamID": "YOUR_APPLE_TEAM_ID",
                    "runScheme": "Release",
                    "bundleAssets": true,
                    "bundleIsDev": false,
                    "plist": {
                        "LSApplicationCategoryType": "YOUR_APP_CATEGORY_TYPE"
                    },
                    "exportOptions": {
                        "method": "app-store",
                        "signingStyle": "automatic",
                        "uploadSymbols": true
                    }
                }
            }
        }
    }
}
```

`renative.json` scheme snippet for manual signing releases

```json
WIP
```

Create **.pkg**:

```
rnv export -p macos -s appstore
```

## Gotchas

-   You might be facing an issue where macOS application window freezes for some time immediately after launching. Solution for that could be:

    -   Open the project in Xcode `(./platformBuilds/[your-app-name]_macos/RNVAppMACOS.xcworkspace)`
    -   Go to `Product` in the menu bar
    -   Click on `Clean Build Folder` in the dropdown
    -   Run the app again