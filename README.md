# MarkdownUI

This is a fork of [Swift Markdown UI](https://github.com/gonzalezreal/swift-markdown-ui).

## Usage

```swift
import MarkdownUI

struct TestView: View {
    var body: some View {
        Markdown("# Heading")
    }
}
```

## Compatibility Notes

If your app uses an older version of Kotlin Multiplatform (e.g., 1.6), you need to remove the arm64 binary to run it on simulators. Using Swift Markdown UI via Swift Package Manager (SPM) does not work in this case because it won’t remove the arm64 binary. Carthage also does not work since [it does not support SPM-only projects](https://github.com/Carthage/Carthage/pull/1945).

This fork of Swift Markdown UI includes the following modifications:

- Added an Xcode project file to explicitly remove arm64 binaries for iOS simulators.
- Utilizes [Apple’s fork of cmark](https://github.com/apple/swift-cmark) to avoid compile errors.

Once your app no longer uses Kotlin Multiplatform or once Carthage supports SPM-only projects, this repository will no longer be necessary.

## Known Issues

- Sources/MarkdownUI/Parser/MarkdownParser.swift file contains some commented-out changes to allow successful compilation. As a result, table support is not stable.
- Once Apple’s fork of cmark exposes these symbols, you can uncomment them.
  - `CMARK_NODE_TABLE`
  - `CMARK_NODE_TABLE_ROW`
  - `CMARK_NODE_TABLE_CELL`
