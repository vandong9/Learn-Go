# BASIC ABOUT GOLANG

Defer: 
- call at end of function
- is stack: first in last execute           
## Data Type
### Basic types:
- bool
- string
- int  int8  int16  int32  int64
- uint uint8 uint16 uint32 uint64 uintptr
- byte // alias for uint8
- rune // alias for int32
      // represents a Unicode code point
- float32 float64
int, uint, uintptr will be 32 or 64 upon systems

complex64 complex128
Variables declared without an explicit initial value are given default value:
- 0 for numeric types,
- false for the boolean type, and
- "" (the empty string) for strings.
- pointer will compare with nil

### Array

### Slice:
- A slice does not store any data, it just describes a section of an underlying array.
- Changing the elements of a slice modifies the corresponding elements of its underlying array.
- Other slices that share the same underlying array will see those changes.
- If the backing array of s is too small to fit all the given values a bigger array will be allocated. The returned slice will point to the newly allocated array.

### Maps
- Only can create by make keyword
- The zero value of a map is nil. A nil map has no keys, nor can keys be added.
- If the top-level type is just a type name, you can omit it from the elements of the literal.
- If elem or ok have not yet been declared you could use a short declaration form: ex: elem, ok := m[key]


### Range
- The range form of the for loop iterates over a slice or map.
- When ranging over a slice, two values are returned for each iteration. The first is the index, and the second is a copy of the element at that index.

### Function
- Functions are values too. They can be passed around just like other values, may be used as function arguments and return values.
- Go functions may be closures. A closure is a function value that references variables from outside its body. The function may access and assign to the referenced variables; in this sense the function is "bound" to the variables, ex: 
	|func adder() func(int) int  => adder is cloure keep function, usage  ad=adder(); ad(10)

## Type
- Can add function to type but MUST use alias AND in same package, can not add function for type defined in other package: type MyInt int

## Custom Type - Struct
- Struct fields are accessed using a dot.
- Struct fields can be accessed through a struct pointer
- Add method for struct ex:
	> func (v Vertex) Scale(f float64) {
	> 	v.X = v.X * f
	>	v.Y = v.Y * f
	> }
	- Above sample, value X, Y will not keep when complete the function, to update value of X, Y in v, use pointer =>  func (v *Vertex) Scale(f float64)


## Interace
- A type implements an interface by implementing its methods. There is no explicit declaration of intent, no "implements" keyword
- Implicit interfaces decouple the definition of an interface from its implementation, which could then appear in any package without prearrangement.
- When inteface assigned to instance, it keep type and value of that instance
- Must check nil before using interace to ensure interface variable was assign to speicific instance
- The interface type that specifies zero methods is known as the empty interface. An empty interface may hold values of any type
- Should check type of interface current refer: f, ok := i.(data type need check)
- Get current data type of interface current refer: v := i.(type)  // type is keyword
		> switch v := i.(type) {
			case T:
				// here v has type T
			case S:
				// here v has type S
			default:
				// no match; here v has the same type as i
		}




## Channel
- Create by make keyword: c := make(chan int <, num>) // num is buffer
- Should check if channel is closed v, ok := <-ch
- The loop for i := range c receives values from the channel repeatedly until it is closed
- Only the sender should close a channel, never the receiver.
- Channels aren't like files; you don't usually need to close them. Closing is only necessary when the receiver must be told there are no more values coming, such as to terminate a range loop.
- The select statement lets a goroutine wait on multiple communication operations.
- A select blocks until one of its cases can run, then it executes that case. It chooses one at random if multiple are ready.
- We can define a block of code to be executed in mutual exclusion by surrounding it with a call to Lock and Unlock as shown on the Inc method.
- We can also use defer to ensure the mutex will be unlocked as in the Value method.




## Constant
Constants are declared like variables, but with the const keyword.
Constants cannot be declared using the := syntax.
can group as 
const (
	aa = 12
	bb = ""
)


## Loop
- Have only one type of loop is for loop
- The init and post statements are optional
- Act like while: At that point you can drop the semicolons: C's while is spelled for in Go.
- If you omit the loop condition it loops forever, so an infinite loop is compactly expressed.

## Condition
- If and else: Variables declared inside an if short statement are also available inside any of the else blocks.

- Switch: 
 - no need add break
 - Switch without a condition is the same as switch true.





