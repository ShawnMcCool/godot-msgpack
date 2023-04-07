
# godot-msgpack

A MessagePack serializer implemented in pure GDScript

- No dependency
- No native binding required

# Installation

Copy the `msgpack.gd` at the root of the repository into your godot project

# Usage

```gdscript
var Msgpack = preload("res://msgpack.gd")

func _myfunc():
    var data = {"type": "wizard", "attack": 10, "weapon": ["dagger", "staff"]}

    var res = Msgpack.encode(data)
    print(res.result) # A PackedByteArray of the data encoded MessagePack

    var res2 = Msgpack.decode(res.result)
    print(res2.result) # Get back the original data
```

## class `Msgpack`

### `static Dictionary encode(Variant value)`

Convert a value (number, string, array and dictionary) into their
counterparts in messagepack. Returns dictionary with three fields:
`result` which is the packed data (a PackedByteArray); `error` which is the
error code; and `error_string` which is a human readable error message

### `static Dictionary decode(PackedByteArray bytes)`

Convert a packed data (a PackedByteArray) back into a value, the reverse of the
encode function. The return value is similar to the one in the encode
method

# Limitation

- Only support null, boolean, integer, float, PackedByteArray, string, array and
  dictionary. No support for other data type like Vector2 and Vector3
- No support for the ext datatype in MessagePack
- Slow compare to the built-in binary serialization in godot

# Testcases

```
godot -s run_test.gd
```

# License

This code was written by `Tintin Ho`. The license is contained within the `msgpack.gd` file.

> Copyright (C) 2019 Tintin Ho
> 
> Permission is hereby granted, free of charge, to any person obtaining a copy
> of this software and associated documentation files (the "Software"), to deal
> in the Software without restriction, including without limitation the rights
> to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
> copies of the Software, and to permit persons to whom the Software is
> furnished to do so, subject to the following conditions:
> 
> The above copyright notice and this permission notice shall be included in all
> copies or substantial portions of the Software.
> 
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
> FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
> AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
> LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
> OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
> SOFTWARE.