struct MemoryAddress<T>: CustomStringConvertible {
    let intValue: Int
    
    var description: String {
        let length = 2 + 2 * MemoryLayout<UnsafeRawPointer>.size
        return String(format: "%0\(length)p", intValue)
    }
    
    init(of structPointer: UnsafePointer<T>) {
        intValue = Int(bitPattern: structPointer)
    }
    
}

extension MemoryAddress where T:AnyObject {
    init(of classInstance: T) {
        intValue = unsafeBitCast(classInstance, to: Int.self)
    }
}

class MyClass {let foo = 42}

var classInstance = MyClass()

let classInstanceAddress = MemoryAddress(of: classInstance)

//print(String(format: "%018p", classInstanceAddress.intValue))
print(classInstanceAddress)

struct MyStruct {let foo = 42}

var structInstance = MyStruct()
let strucInstanceAddress = MemoryAddress(of: &structInstance)
//print(String(format: "%018p", strucInstanceAddress.intValue))
print(strucInstanceAddress)
