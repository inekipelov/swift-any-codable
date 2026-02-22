# AnyCodable

Type-erased wrappers for `Encodable`, `Decodable`, and `Codable` values.

<p align="center">
  <a href="https://swift.org"><img src="https://img.shields.io/badge/Swift-5.1+-F05138?logo=swift&logoColor=white" alt="Swift 5.1+"></a>
  <a href="https://developer.apple.com"><img src="https://img.shields.io/badge/iOS-9.0+-000000?logo=apple" alt="iOS 9.0+"></a>
  <a href="https://developer.apple.com"><img src="https://img.shields.io/badge/macOS-10.10+-000000?logo=apple" alt="macOS 10.10+"></a>
  <a href="https://developer.apple.com"><img src="https://img.shields.io/badge/tvOS-9.0+-000000?logo=apple" alt="tvOS 9.0+"></a>
  <a href="https://developer.apple.com"><img src="https://img.shields.io/badge/watchOS-2.0+-000000?logo=apple" alt="watchOS 2.0+"></a>
</p>

## Installation

### Swift Package Manager

Add the package to your target dependencies in `Package.swift`:

```swift
import PackageDescription

let package = Package(
    name: "YourProject",
    dependencies: [
        .package(url: "https://github.com/inekipelov/swift-any-codable.git", branch: "main")
    ],
    targets: [
        .target(
            name: "YourTarget",
            dependencies: [
                .product(name: "AnyCodable", package: "swift-any-codable")
            ]
        )
    ]
)
```

Then import the module:

```swift
import AnyCodable
```

## Usage

### AnyEncodable

```swift
import AnyCodable

let dictionary: [String: AnyEncodable] = [
    "boolean": true,
    "integer": 1,
    "double": 3.141592653589793,
    "string": "string",
    "array": [1, 2, 3],
    "nested": [
        "a": "alpha",
        "b": "bravo",
        "c": "charlie"
    ],
    "null": nil
]

let encoder = JSONEncoder()
let json = try! encoder.encode(dictionary)
```

### AnyDecodable

```swift
let json = """
{
    "boolean": true,
    "integer": 1,
    "double": 3.141592653589793,
    "string": "string",
    "array": [1, 2, 3],
    "nested": {
        "a": "alpha",
        "b": "bravo",
        "c": "charlie"
    },
    "null": null
}
""".data(using: .utf8)!

let decoder = JSONDecoder()
let dictionary = try! decoder.decode([String: AnyDecodable].self, from: json)
```

### AnyCodable

`AnyCodable` can be used to wrap values for encoding and decoding.

## References

- Original idea: [Flight-School / AnyCodable](https://github.com/Flight-School/AnyCodable)
- Author: [mattt](https://github.com/mattt)
