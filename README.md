# SwiftUIAppIcons

A comprehensive guide to implementing app icons in SwiftUI projects with support for different appearance modes.

<!-- Add your app icon previews here -->
<!-- Example: ![App Icon Preview](assets/app-icon-preview.png) -->

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Adding App Icons to Your SwiftUI Project](#adding-app-icons-to-your-swiftui-project)
  - [Preparing Your Icon Assets](#preparing-your-icon-assets)
  - [Adding Icons to the Asset Catalog](#adding-icons-to-the-asset-catalog)
  - [Supporting Different Appearance Modes](#supporting-different-appearance-modes)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## Overview

SwiftUIAppIcons demonstrates how to properly implement app icons in a SwiftUI project, with support for multiple appearance modes including Any Appearance, Dark, and Tinted modes. This project serves as a template and guide for developers wanting to implement professional-grade app icons in their iOS applications using Xcode's modern asset catalog system.

## Features

- Complete implementation of app icons for iOS applications
- Support for different appearance modes (Any Appearance, Dark Mode, Tinted Mode)
- Example assets at all required resolutions
- Step-by-step guide for implementation

## Requirements

- iOS 14.0+
- Xcode 13.0+
- Swift 5.5+

## Adding App Icons to Your SwiftUI Project

### Preparing Your Icon Assets

1. **Create your master icon** at 1024×1024 pixels resolution in PNG format
   - Use the 32-bit PNG format with alpha channel
   - Ensure you're using sRGB color space
   - Do not include rounded corners or drop shadows (iOS will add these automatically)
   - Design separate icons for different appearance modes if needed

2. **Export your icons as PNG files**
   - Primary resolution: 1024×1024 pixels (required for App Store)
   - You can let Xcode generate all other sizes, or provide custom versions for better control

3. **Organize your files** in a folder structure for easy management

### Adding Icons to the Asset Catalog

1. **Open your project** in Xcode

2. **Navigate to the Asset Catalog**
   - Select `Assets.xcassets` in the Project Navigator
   - If you don't have an asset catalog, create one by right-clicking the project navigator and selecting `New File > Asset Catalog`

3. **Add an App Icon Set**
   - Right-click in the Asset Catalog and select `New App Icon`
   - This creates an `AppIcon` asset set (displays as `AppIcon.appiconset` in the file structure)

4. **Configure the App Icon for Multiple Appearance Modes**
   - In the modern Xcode interface, the App Icon editor now supports different appearance modes directly
   - You'll see three sections: "Any Appearance," "Dark," and "Tinted"
   - Each section accepts a 1024x1024 PNG icon that will be automatically scaled to all required sizes

5. **Add your icons**
   - Drag and drop your PNG icons into each appearance mode section:
     - Add your standard icon to the "Any Appearance" section
     - Add your dark-optimized icon to the "Dark" section
     - Add your tinted version to the "Tinted" section
   - Xcode will automatically generate all required sizes for iOS (displayed as "iOS 1,024pt" at the bottom)

### Supporting Different Appearance Modes

The modern Xcode asset catalog handles appearance mode switching automatically. The system will display the appropriate icon based on the user's appearance mode settings without requiring additional code.

1. **Ensure all appearance slots are filled**
   - For best results, provide custom icons for each appearance mode
   - If a specific mode doesn't have a custom icon, iOS will use the "Any Appearance" icon

2. **Test with different appearance settings**
   - Use the Xcode simulator or a device to verify that your icons switch correctly when changing appearance modes
   - You can quickly test different modes in the simulator via Settings > Developer > Appearance

```swift
// Example code to programmatically set the app icon (requires user permission)
if UIApplication.shared.supportsAlternateIcons {
    UIApplication.shared.setAlternateIconName("AppIcon-Dark") { error in
        if let error = error {
            print("Error setting alternate icon: \(error.localizedDescription)")
        }
    }
}
```

## Best Practices

- **Keep your icon simple and recognizable** at small sizes
- **Test your icon** on different devices and in different contexts
- **Consider accessibility** and how your icon appears to users with visual impairments
- **Use vector-based design tools** for initial creation, then export to PNG
- **Maintain consistency** across different appearance modes while adapting for visibility
- **Follow Apple's Human Interface Guidelines** for app icons

## Troubleshooting

**Icon not appearing in the simulator**
- Clean your build folder (Shift+Command+K)
- Delete the app from the simulator and reinstall
- Make sure the AppIcon is selected in your target's settings under "General > App Icons and Launch Screen"

**Icon appears pixelated**
- Ensure you're using high-resolution PNG files (1024x1024px)
- Let Xcode handle the resizing rather than providing pre-scaled assets

**Icon appearance mode not switching**
- Verify that you've correctly added icons to all appearance mode slots
- Check if the device/simulator is actually changing appearance modes (Settings > Display & Brightness)
- Restart the app after changing appearance settings

**Missing appearance mode sections in Xcode**
- Make sure you're using a recent version of Xcode that supports multiple appearance modes for app icons
- If you don't see the appearance mode options, check for Xcode updates

## License

SwiftUIAppIcons is available under the MIT license. See the LICENSE file for more info.

---

*This project is maintained by Shahinur Rahman. For questions or support, please open an issue in the repository.*
