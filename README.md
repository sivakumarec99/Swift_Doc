# Swift_Doc
Shot Reading , Swift Document reading Short Cuts

🔹 About Swift
	•	✅ Modern & Powerful: Safe, fast, and expressive language for all platforms.
	•	🚀 Optimized: Compiler and syntax designed for both performance and development ease.
	•	👶👨‍💻 Beginner-friendly: Easy to learn, but powerful enough for pros.
	•	🧠 Error-safe by design:
	•	Variables must be initialized
	•	Array bounds checked
	•	Integer overflow checked
	•	Optionals prevent nil misuse
	•	Auto memory management
	•	Built-in error handling
	•	⚙️ Performance-first: Optimized for modern hardware and efficient code.
	•	✨ Clear & Concise: Lightweight syntax, type inference, and pattern matching.
	•	🔁 Evolving Language: Constantly improving with community-driven features.
	•	🧩 Versatile Use: Great for scripts, apps, servers—even OS-level code.

🔹 Swift Version Compatibility
	•	📘 Current Version: Swift 6.1 (default in Xcode 16.3).
	•	🔄 Backward Compatible: Builds code from Swift 6.1, 5, 4.2, and 4.
	•	🌟 New Features in Older Modes:
	•	Swift 6.1 features may work in Swift 5 mode (some via feature flags).
	•	Strict concurrency needs Swift 6.1 mode.
	•	⚠️ Swift 5-only Features:
	•	Opaque return types need Swift 5.1 runtime.
	•	try? no longer adds extra optional.
	•	Large integer literals infer correct types.
	•	Concurrency needs Swift 5 + updated standard library + iOS 13+/macOS 10.15+.
	•	🧩 Mixed Version Support:
	•	Targets in Swift 6.1 can depend on Swift 5/4.2/4, and vice versa.
	•	Enables gradual migration in large projects.


Swift :: 

Hello, World!: Single-line program with print("Hello, world!"). No main() or semicolons needed.
Variables and Constants:
var for variables, let for constants.
Type inference or explicit types (e.g., let explicitDouble: Double = 70).
No implicit type conversion; use explicit conversion (e.g., String(width)).


Strings:
String interpolation with \() (e.g., "I have \(apples) apples.").
Multi-line strings with """ (indentation ignored if matching closing quotes).


Collections:
Arrays: ["strawberries", "limes"], mutable with .append().
Dictionaries: ["Malcolm": "Captain"], access via keys.
Empty collections: [] or [:], with explicit types if needed (e.g., [String: Float]).


Control Flow:
Conditionals: if, switch (no implicit fallthrough, exhaustive with default).
Loops: for-in, while, repeat-while.
Optionals: Handle nil with if let, ??, or shorthand unwrapping.


Functions and Closures:
Declare with func, optional argument labels (e.g., _ person).
Closures: Inline with {}, concise syntax (e.g., numbers.map { $0 * 3 }).
Functions as first-class types; can return or take functions.


Objects and Classes:
Classes with class, properties, methods, and init.
Subclasses with override, computed properties with get/set.
willSet/didSet for property observation.


Enumerations and Structures:
Enums: enum Rank, raw values (e.g., Int), or associated values.
Structs: Value types, copied when passed (unlike classes).


Concurrency:
Async functions with async, called with await.
Parallel tasks with async let, structured concurrency with Task or task groups.
Actors for safe concurrent access (e.g., actor ServerConnection).


Protocols and Extensions:
Protocols define requirements (e.g., var simpleDescription: String { get }).
Extensions add functionality to existing types (e.g., extension Int).


Error Handling:
Errors adopt Error protocol, thrown with throw.
Handle with do-catch, try?, or defer for cleanup.


Generics:
Generic functions/types with <T> (e.g., makeArray<Item>).
Constraints with where (e.g., T: Equatable).



Sample Code
Below is a comprehensive Swift program demonstrating key features:
// Simple Values and Strings
let constantFloat: Float = 4.0
var apples = 3
let greeting = "I have \(apples) apples and a value of \(constantFloat * 2)."

// Multi-line String
let multiLine = """
    This is a multi-line string.
    It preserves line breaks.
    I have \(apples) apples.
    """

// Arrays and Dictionaries
var fruits = ["apple", "banana", "orange"]
fruits.append("grape")
var jobs = ["Alice": "Engineer", "Bob": "Designer"]
jobs["Charlie"] = "Manager"

// Control Flow
let scores = [60, 40, 80, 20]
var totalScore = 0
for score in scores {
    totalScore += score > 50 ? 3 : 1
}
let celebration = if totalScore > 10 { "🎉" } else { "" }

// Optionals
var optionalName: String? = "Alice"
let message = "Hello, \(optionalName ?? "Guest")"

// Switch with Enum
enum Suit {
    case spades, hearts, diamonds, clubs
    func color() -> String {
        switch self {
        case .spades, .clubs: return "black"
        case .hearts, .diamonds: return "red"
        }
    }
}
let suit = Suit.hearts
print("Suit: \(suit.color())") // Prints "red"

// Functions
func greet(_ name: String, special: String) -> String {
    return "Hello \(name), today's special is \(special)."
}
print(greet("Alice", special: "sushi"))

// Closures
let numbers = [1, 2, 3, 4]
let tripled = numbers.map { number in number * 3 }
print("Tripled: \(tripled)") // Prints "[3, 6, 9, 12]"

// Classes
class Circle: NamedShape {
    var radius: Double
    init(radius: Double, name: String) {
        self.radius = radius
        super.init(name: name)
    }
    func area() -> Double {
        return .pi * radius * radius
    }
    override func simpleDescription() -> String {
        return "A circle with radius \(radius)."
    }
}
let circle = Circle(radius: 5.0, name: "my circle")
print(circle.simpleDescription()) // Prints "A circle with radius 5.0."

// Concurrency
actor UserManager {
    var users: [Int: String] = [:]
    func addUser(id: Int, name: String) {
        users[id] = name
    }
}
Task {
    let manager = UserManager()
    await manager.addUser(id: 1, name: "Alice")
}

// Protocol and Extension
protocol Describable {
    var description: String { get }
}
extension Double {
    var absoluteValue: Double {
        return self < 0 ? -self : self
    }
}
print((-5.5).absoluteValue) // Prints "5.5"

// Error Handling
enum NetworkError: Error {
    case timeout
}
func fetchData(from url: String) throws -> String {
    if url.isEmpty { throw NetworkError.timeout }
    return "Data from \(url)"
}
do {
    let data = try fetchData(from: "example.com")
    print(data)
} catch {
    print("Error: \(error)")
}

// Generics
func commonElements<T: Sequence, U: Sequence>(_ lhs: T, _ rhs: U) -> [T.Element]
    where T.Element: Equatable, T.Element == U.Element {
    var result: [T.Element] = []
    for lhsItem in lhs {
        for rhsItem in rhs {
            if lhsItem == rhsItem && !result.contains(lhsItem) {
                result.append(lhsItem)
            }
        }
    }
    return result
}
print(commonElements([1, 2, 3], [2, 3, 4])) // Prints "[2, 3]"

This code showcases Swift’s core features, including type inference, optionals, control flow, object-oriented programming, concurrency, protocols, error handling, and generics, providing a practical starting point for learning Swift.

