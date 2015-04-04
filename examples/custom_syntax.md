Custom Types Json
------------------

Custom syntax for Unreal Engine4 configures the C++ output to use these types
for vectors, strings, and shared references.

https://docs.unrealengine.com/latest/INT/API/Runtime/Core/Containers/FString/index.html

@unrealtypes.json
```json
{
	"vector"   : {
		"template": "TArray<%s>",
		"append"  : "Emplace",
		"len"     : "Num"
	},
	"string" : {
		"type": "FString",
		"new" : "TEXT(%s)",
		"len" : "Len"
	},
	"shared" : {
		"template" : "TSharedRef<%s>",
		"type"     : "TSharedRef",
		"reset"    : "Reset"
	}
}
```

The code below inside the `with syntax` block uses the custom template above.
Instead of the default `std::vector` the vectors below will be constructed as `TArray`
from the UnrealEngine C++ API.

https://docs.unrealengine.com/latest/INT/API/Runtime/Core/Containers/TArray/index.html


```rusthon
#backend:c++


with syntax('unrealtypes.json'):
	class A:
		def __init__(self, x:int, y:string):
			self.x = x
			self.y = y

	def foo( s:string, ob:A ) ->A:
		print s
		return ob

	def main():
		v1 = []int(1,2,3,4,5,6)
		v2 = []string( "hello", "world" )
		v1.append( 100 )
		v2.append( "xxx" )
		len(v1)
		s = "foobar"
		len(s)

		a = A()
		foo( v2[0], a )
		v3 = []A( a, a, a )

```