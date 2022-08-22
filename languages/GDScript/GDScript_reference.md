<a name="TOP"></a>

# <b>GDScript（for Godot 4.0）基礎文法</b>
[ [Godot Study Notes 🔰](https://github.com/mubirou/Godot#godot-study-notes) ]  

### <b>INDEX</b>

* Hello,world! （~~[Linux](https://github.com/mubirou/HelloWorld/blob/master/languages/GDScript/GDScript_linux.md#gdscript-linux-)~~ / [Windows](https://github.com/mubirou/HelloWorld/blob/master/languages/GDScript/GDScript_win.md#gdscript-windows-)）
* [コメントアウト](#コメントアウト)
* [データ型](#データ型)
* [データ型の操作](#データ型の操作)
* [クラス](#クラス)
* [基本クラスと派生クラス](#基本クラスと派生クラス)
* [名前空間](#名前空間)
* [継承と委譲](#継承と委譲)
* [変数とスコープ](#変数とスコープ)
* [アクセサ（getter / setter）](#アクセサ)
* [演算子](#演算子)
* [定数](#定数)
* [関数](#関数)
* [匿名関数](#匿名関数)
* [静的変数・静的関数](#静的変数・静的関数)
* [if 文](#if文)
* [三項演算子](#三項演算子)
* [match 文](#match文) ≒ switch 文
* [for 文](#for文)
* [while 文](#while文)
* [配列](#配列)
* [連想配列（辞書）](#連想配列（辞書）)
* [self](#self) ≒ this
* [文字列の操作](#文字列の操作)
* [正規表現](#正規表現)
* [抽象クラス](#抽象クラス)
* [super キーワード](#superキーワード)
* [オーバーライド](#オーバーライド)
* [カスタムイベント](#202207130930)
* [数学関数](#数学関数)
* [乱数](#乱数)
* [日時情報](#202207130907)
* [タイマー](#タイマー)
* [処理速度計測](#処理速度計測)
* [外部テキストの読み込み](#外部テキストの読み込み)

***

<a name="コメントアウト"></a>
# <b>コメントアウト</b>

### 1行コメントアウト

```gdscript
# 〇〇〇〇〇
```

```gdscript
var _x = 1 + 1 # 〇〇〇〇〇
```

### 複数行コメントアウト

```gdscript
# 〇〇〇〇〇
# 〇〇〇〇〇
```

```gdscript
"""
〇〇〇〇〇
〇〇〇〇〇
"""
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%82%B3%E3%83%A1%E3%83%B3%E3%83%88%E3%82%A2%E3%82%A6%E3%83%88)]  
参考：[GODOT DOCS（コメントの間隔）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_styleguide.html?highlight=comment#comment-spacing)  
参考：[Pythonのコメント](https://note.nkmk.me/python-comment/)  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月01日  
更新日：2022年08月13日  
[[TOP](#TOP)]


<a name="データ型"></a>
# <b>データ型</b>

<a name="typeof()の戻り値一覧"></a>
### [typeof()](#typeof()関数) の戻り値一覧  

|番号|データ型|TYPE_*|内容|
|:--:|:--|:--|:--|
|0|[null](https://bit.ly/3K8PxOu)|TYPE_NIL|[**内容がない**](#TYPE_NIL)|
|1|[bool](https://bit.ly/3QGNq6Y)|TYPE_BOOL|[**論理型**](#TYPE_BOOL)|
|2|[int](https://bit.ly/3c8lGZX)|TYPE_INT|[**整数型**](#TYPE_INT)|
|3|[float](https://bit.ly/3dIQhxN)|TYPE_FLOAT|[**浮動小数点数**](#TYPE_FLOAT)|
|4|[String](https://bit.ly/3cbXwOk)|TYPE_STRING|[**文字列**](#TYPE_STRING)|
|5|[Vector2](https://bit.ly/3AzKTWF)|TYPE_VECTOR2|
|6|[Vector2i](https://bit.ly/3KbsfHW)|TYPE_VECTOR2I|
|7|[Rect2](https://bit.ly/3PAWNnl)|TYPE_RECT2|
|8|[Rect2i](https://bit.ly/3QF1EFg)|TYPE_RECT2I|
|9|[Vector3](https://bit.ly/3Ch8koX)|TYPE_VECTOR3|
|10|[Vector3i](https://bit.ly/3AzL0Bz)|TYPE_VECTOR3I|
|11|[Transform2D](https://bit.ly/3wiQmhR)|TYPE_TRANSFORM2D|
|12|[]()|TYPE_VECTOR4|
|13|[]()|TYPE_VECTOR4I|
|14|[Plane](https://bit.ly/3A6FV2d)|TYPE_PLANE|
|15|[Quaternion](https://bit.ly/3QXfd2N)|TYPE_QUATERNION|
|16|[AABB](https://bit.ly/3dEWAlQ)|TYPE_AABB|
|17|[Basis](https://bit.ly/3Aa7LKT)|TYPE_BASIS|
|18|[Transform3D](https://bit.ly/3R0wrft)|TYPE_TRANSFORM3D|
|19|[]()|TYPE_PROJECTION|
|20|[Color](https://bit.ly/3dG5K1q)|TYPE_COLOR|
|21|[StringName](https://bit.ly/3QFkjB5)|TYPE_STRING_NAME|
|22|[NodePath](https://bit.ly/3K5MczK)|TYPE_NODE_PATH|
|23|[RID](https://bit.ly/3Pw5TSo)|TYPE_RID|
|24|[Object](https://bit.ly/3PCb2IC)|TYPE_OBJECT|[**クラス**](#TYPE_OBJECT)|
|25|[Callable](https://bit.ly/3A9SHwN)|TYPE_CALLABLE|
|26|[Signal](https://bit.ly/3T4MFpJ)|TYPE_SIGNAL|
|27|[Dictionary](https://bit.ly/3T4BZYb)|TYPE_DICTIONARY|[**辞書型･連想配列**](#TYPE_DICTIONARY)|
|28|[Array](https://bit.ly/3CrSTtU)|TYPE_ARRAY|[**配列**](#TYPE_ARRAY)|
|29|[PackedByteArray](https://bit.ly/3SZ3in3)|TYPE_PACKED_BYTE_ARRAY|
|30|[PackedInt32Array](https://bit.ly/3PC8b2g)|TYPE_PACKED_INT32_ARRAY|
|31|[PackedInt64Array](https://bit.ly/3dxZh8C)|TYPE_PACKED_INT64_ARRAY|
|32|[PackedFloat32Array](https://bit.ly/3QVeaQJ)|TYPE_PACKED_FLOAT32_ARRAY|
|33|[PackedFloat64Array](https://bit.ly/3KaCtYI)|TYPE_PACKED_FLOAT64_ARRAY|
|34|[PackedStringArray](https://bit.ly/3AAajU7)|TYPE_PACKED_STRING_ARRAY|
|35|[PackedVector2Array](https://bit.ly/3pvA811)|TYPE_PACKED_VECTOR2_ARRAY|
|36|[PackedVector3Array](https://bit.ly/3Cklam8)|TYPE_PACKED_VECTOR3_ARRAY|
|37|[PackedColorArray](https://bit.ly/3CfYlA3)|TYPE_PACKED_COLOR_ARRAY|
|38|[Variant.Type](https://bit.ly/3c9GDno)|TYPE_MAX|

<a name="TYPE_NIL"></a>
### 👉 null…内容がないことを示す定数
```gdscript
var _something
print(_something) #-> null
print(typeof(_something)) #-> 0
print(typeof(_something) == TYPE_NIL) #-> true
print(_something == null) #-> true
```

<a name="TYPE_BOOL"></a>
### 👉 論理型（bool）
* trueまたはfalse
```gdscript
var _bool = true # True/Falaseは不可
print(_bool) #-> true
print(typeof(_bool)) #-> 1
print(typeof(_bool) == TYPE_BOOL) #-> true
print(_bool is bool) #-> true
```

<a name="TYPE_INT"></a>
### 👉 整数型（int）
* 約±922京まで扱えます
```gdscript
var _int = 9223372036854775807 # ±9223372036854775807まで扱える
print(_int) #-> 9223372036854775807
print(typeof(_int)) #-> 2
print(typeof(_int) == TYPE_INT) #-> true
print(_int is int) #-> true
```

<a name="TYPE_FLOAT"></a>
### 👉 浮動小数点数（float）
* 小数点第6桁まで
```gdscript
var _float = 3.141592653589793238462643383279502884197169399375105820974944592307816406286
print(_float) #-> 3.14159265358979（小数点第14桁まで）
print(typeof(_float)) #-> 3
print(typeof(_float) == TYPE_FLOAT) #-> true
print(_float is float) #-> true
```

<a name="TYPE_STRING"></a>
### 👉 文字列（String）
```gdscript
var _string = "あいうえお" # '〇〇'でも可
print(_string) #-> あいうえお
print(typeof(_string)) #-> 4
print(typeof(_string) == TYPE_STRING) #-> true
print(_string is String) #-> true
```

<a name="TYPE_OBJECT"></a>
### 👉 クラス（Object）
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
class MyClass: #前方宣言でなくてもよい
	pass

func _ready():
	……
	var _myClass = MyClass.new()
	print(_myClass) #-> [RefCounted:-92233720120XXXXXXXX]
	print(typeof(_myClass)) #-> 24
	print(typeof(_myClass) == TYPE_OBJECT) #-> true
	print(_myClass is Object) #-> true
```

<a name="TYPE_DICTIONARY"></a>
### 👉 辞書型（Dictionary） : 連想配列
```gdscript
var _dic = {"A":"あ", "I":"い"}
print(_dic) #-> {"A":"あ", "I":"い"}
print(typeof(_dic)) #-> 27
print(typeof(_dic) == TYPE_DICTIONARY) #-> true
print(_dic is Dictionary) #-> true
```

<a name="TYPE_ARRAY"></a>
### 👉 配列（Array）
```gdscript
var _array = ["A", "I", "U"]
print(_array) #-> ["A", "I", "U"]
print(typeof(_array)) #-> 28
print(typeof(_array) == TYPE_ARRAY) #-> true
print(_array is Array) #-> true
``` 

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%83%87%E3%83%BC%E3%82%BF%E5%9E%8B)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
参考：[GODOT DOCS（**Variant.Type**）](https://bit.ly/3K6kGSC)  
作成者：夢寐郎  
作成日：2022年01月03日  
更新日：2022年08月20日  
[[TOP](#TOP)]


<a name="データ型の操作"></a>
# <b>データ型の操作</b>

<a name="typeof()関数"></a>

### 👉 typeof() 関数
* データ型を返す（[戻り値一覧](#typeof()の戻り値一覧)）

```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	print(typeof(true)) #-> 1（== TYPE_BOOL）
	print(typeof(100)) #-> 2（== TYPE_INT）
	print(typeof(0.1)) #-> 3（== TYPE_FLOAT）
	print(typeof("1")) #-> 4（== TYPE_STRING）
	print(typeof(["A", "B", "C"])) #-> 28（== TYPE_ARRAY）
	print(typeof({"ICHIRO":54, "HANAKO":"15"})) #-> 27（== TYPE_DICTIONARY）
	print(typeof(MyClass.new())) #-> 24（== TYPE_OBJECT）

class MyClass:
	pass
```

###  👉 is 演算子
* データ型を判断する（[データ型一覧](#typeof()の戻り値一覧)）
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	print(true is bool) #-> true
	print(100 is int) #-> true
	print(0.1 is float) #-> true
	print("1" is String) #-> true
	print(["A", "B", "C"] is Array) #-> true
	print({"ICHIRO":54, "HANAKO":"15"} is Dictionary) #-> true

	var _myClass = MyClass.new()
	print(_myClass is Object) #-> true
	print(_myClass is MyClass) #-> true

class MyClass:
	pass
```

###  👉 as 演算子
* Godot 3.x と異なり失敗するとエラーになる（**要調査**）
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	print(1 as bool) #-> True
	#print("123" as int) #-> Invalid cast: could not convert value to 'int'.
	#print("X12Y34" as int) #-> Invalid cast: could not convert value to 'int'.
	
	var _hogeClass = HogeClass.new()
	#print(_hogeClass as FugaClass) #-> Parser Error

class HogeClass:
	pass

class FugaClass:
	pass
```

###  👉 データ型のキャスト（数値 ⇔ bool型）
```gdscript
# 数値（int）型 → bool型
var _tmp = bool(1)
print(_tmp) #-> true
print(typeof(_tmp)) #-> 1（== TYPE_BOOL）

# bool型 → 数値（int）型
_tmp = int(true)
print(_tmp) #-> 1
print(typeof(_tmp)) #-> 2（== TYPE_INT）
```

###  👉 データ型のキャスト（数値 ⇔ String 型）

* **String 型 → 数値**
	* ⚠ Godot 4.0 では **int("〇〇")** は不可（[参考](https://bit.ly/3AAB4aZ)）
	* [String → 整数] は [**String.to_int()**](https://bit.ly/3PEn1oX) で可能
	* [String → 浮動小数点数] は [**String.to_float()**](https://bit.ly/3QFiILz) で可能

```gdscript
print("001".to_int()) #-> 1
print("X12Y34".to_int()) #-> 1234

var _string = "3.141592653589793238462643383279502884197169399375105820974944592307816406286"
print(_string.to_float()) #-> 3.14159265358979（小数点第14桁まで）
```

* **数値 → String 型**
```gdscript
var _tmp = str(100)
print(_tmp) #-> "100"
print(typeof(_tmp)) #-> 4（== TYPE_STRING）
```

### 👉 基数変換
* **10進整数 ⇆ 16進整数**
	* 10進整数 → 16進整数
	```gdscript
	print("%x" % 29) #-> 1d（String型）
	print("%X" % 29) #-> 1D（String型）
	```
	* 16進整数 → 10進整数
	```gdscript
	print("1d".hex_to_int()) #-> 29（int型）
	```

* **10進整数 ⇆ 2進整数**
	* 10進整数 → 2進整数（**要調査**）
	```gdscript
	# /root/Main(Main.gd)
	extends Node3D
	……
	func _ready():
		……
		print(int2bin(0)) #-> 0（int型）
		print(int2bin(2)) #-> 10（int型）
		print(int2bin(100)) #-> 1100100（int型）
		print(int2bin(524287)) #-> 1111111111111111111（int型）

	func int2bin(arg):
		if (arg > 524287) or (arg < 0):
			assert(false, "Error: 0～524287 のみ処理可能")
		var _binary = ""
		var _temp:int
		var _count = 31 # Checking up to 32 bits 
		while(_count >= 0):
			_temp = arg >> _count # Bit shifting
			if _temp & 1: # Bitwise AND
				_binary += "1" 
			else: 
				_binary += "0" 
			_count -= 1 
		return _binary.to_int()
	```
	* 2進整数 → 10進整数
	```gdscript
	print("11101".bin_to_int()) #-> 29（int型）
	print("%d" % 0b11101) #-> 29（String型）
	print(0b11101) #-> 29（int型）
	```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%83%87%E3%83%BC%E3%82%BF%E5%9E%8B%E3%81%AE%E6%93%8D%E4%BD%9C)]  
参考：[GODOT DOCS（**Padding**）](https://bit.ly/3CnLxYI)  
参考：[GODOT DOCS（**String**)](https://bit.ly/3dKy3vL)  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月13日  
更新日：2022年08月21日  
[[TOP](#TOP)]


<a name="クラス"></a>
# <b>クラス</b>

### 👉「クラスファイル」を使う方法
[.gd ファイルがクラス！](http://puggygame.blogspot.com/2018/03/gdscript.html)になる（class キーワードは記述しない）  

#### クラスの定義
```gdscript
# res://Rectangle.gd（クラスファイル）
class_name Rectangle # ファイル名と別名でも可
# 👆 var Rectangle = load("res://Rectangle.gd") が不要になる

# 疑似プライベート変数
var __width
var __height

var width: # getter/setter
	get: return __width
	set(value): __width = value
	
var height: # getter/setter
	get: return __height
	set(value): __height = value

func getArea(): # 公開関数（面積計算用）
	return __width * __height

func _init(w,h): # コンストラクタ
	__width = w
	__height = h
```

#### 実行
```gdscript
# /root/Main(Main.gd)
extends Node3D
……	
func _ready():
	……
	var _rectangle = Rectangle.new(640, 480)

	# プロパティの取得
	print(_rectangle.width) #-> 640
	print(_rectangle.height) #-> 480

	# プロパティの更新
	_rectangle.width = 1920
	_rectangle.height = 1080

	# プロパティの取得（再度）
	print(_rectangle.width) #-> 1920
	print(_rectangle.height) #-> 1080

	# 関数の実行
	print(_rectangle.getArea()) #-> 2073600
```

### 👉「内部クラス」を使う方法
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
class Rectangle: # 長方形クラス
	# 疑似プライベート変数
	var __width
	var __height
	
	var width: # getter/setter
		get: return __width
		set(value): __width = value
		
	var height: # getter/setter
		get: return __height
		set(value): __height = value

	func getArea(): # 公開関数（面積計算用）
		return __width * __height
	
	func _init(w,h): # コンストラクタ
		__width = w
		__height = h
	
func _ready():
	……
	var _rectangle = Rectangle.new(640, 480)

	# プロパティの取得
	print(_rectangle.width) #-> 640
	print(_rectangle.height) #-> 480

	# プロパティの更新
	_rectangle.width = 1920
	_rectangle.height = 1080

	# プロパティの取得（再度）
	print(_rectangle.width) #-> 1920
	print(_rectangle.height) #-> 1080

	# 関数の実行
	print(_rectangle.getArea()) #-> 2073600
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%82%AF%E3%83%A9%E3%82%B9)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月04日  
作成日：2022年08月20日  
[[TOP](#TOP)]


<a name="基本クラスと派生クラス"></a>
# <b>基本クラスと派生クラス</b>

### 👉「クラスファイル」を継承する方法
[.gd ファイルがクラス！](http://puggygame.blogspot.com/2018/03/gdscript.html)になる（class キーワードは記述しない）  

#### SuperClass（基本クラス）の定義
```gdscript
# res://SuperClass.gd（基本＝基底クラス）
class_name SuperClass
# 継承時に extends "res://SuperClass.gd" ではなく簡略できる

# 疑似プライベート変数
var __pSuper = "基本クラスのプロパティ"

var pSuper: # getter/setter
	get: return __pSuper
	set(value): __pSuper = value

func mSuper(): # 関数
	return "基本クラスのメソッド"
	
func _init():
	print("SuperClass._init()")
```

#### SubClassA（派生クラスＡ）の定義
```gdscript
# res://SubClassA.gd（派生クラスＡ）
class_name SubClassA extends SuperClass # extends 以降を別行にしても可能

# 疑似プライベート変数
var __pSubA = "派生クラスＡのプロパティ"

var pSubA: # getter/setter
	get: return __pSubA
	set(value): __pSubA = value

func mSubA(): # 関数
	return "派生クラスＡのメソッド"

func _init():
	print("SubClassA._init()")
```

#### SubClassB（派生クラスＢ）の定義
```gdscript
# res://SubClassB.gd（派生クラスＢ）
class_name SubClassB extends SuperClass # extends 以降を別行にしても可能

# 疑似プライベート変数
var __pSubB = "派生クラスＢのプロパティ"

var pSubB: # getter/setter
	get: return __pSubB
	set(value): __pSubB = value

func mSubB(): # 関数
	return "派生クラスＢのメソッド"

func _init():
	print("SubClassB._init()")
```

#### 実行
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	load("res://SubClassA.gd")
	var _subClassA = SubClassA.new() #-> SubClassA._init()
	print(_subClassA) #-> [RefCounted:-9223372011789614097]
	print(_subClassA is SubClassA) #-> true（＝SubClassA型）
	print(_subClassA is load("res://SuperClass.gd")) #-> true（＝SuperClass型）
	print(_subClassA.pSubA) #-> 派生クラスＡのプロパティ
	print(_subClassA.pSuper) #-> 基本クラスのプロパティ
	print(_subClassA.mSubA()) #-> 派生クラスＡのメソッド
	print(_subClassA.mSuper()) #-> 基本クラスのメソッド
	
	load("res://SubClassB.gd")
	var _subClassB = SubClassB.new() #-> SubClassB._init()
	print(_subClassB) #-> [RefCounted:-9223372011772836883]
	print(_subClassB is SubClassB) #-> true（＝SubClassB型）
	print(_subClassB is load("res://SuperClass.gd")) #-> true（＝SuperClass型）
	print(_subClassB.pSubB) #-> 派生クラＢのプロパティ
	print(_subClassB.pSuper) #-> 基本クラスのプロパティ
	print(_subClassB.mSubB()) #-> 派生クラスＢのメソッド
	print(_subClassB.mSuper()) #-> 基本クラスのメソッド
```

### 👉「内部クラス」を使う方法
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
#===============================
# SuperClass（基本クラス）の定義
#===============================
class SuperClass:
	# 疑似プライベート変数
	var __pSuper = "基本クラスのプロパティ"

	var pSuper: # getter/setter
		get: return __pSuper
		set(value): __pSuper = value

	func mSuper(): # 関数
		return "基本クラスのメソッド"

	func _init():
		pass

#================================
# SubClassA（派生クラスＡ）の定義
#================================
class SubClassA extends SuperClass:
	# 疑似プライベート変数
	var __pSubA = "派生クラスＡのプロパティ"

	var pSubA: # getter/setter
		get: return __pSubA
		set(value): __pSubA = value

	func mSubA(): # 関数
		return "派生クラスＡのメソッド"

	func _init():
		print("SubClassA._init()")

#================================
# SubClassB（派生クラスＢ）の定義
#================================
class SubClassB extends SuperClass:
	# 疑似プライベート変数
	var __pSubB = "派生クラスＢのプロパティ"

	var pSubB: # getter/setter
		get: return __pSubB
		set(value): __pSubB = value

	func mSubB(): # 関数
		return "派生クラスＢのメソッド"

	func _init():
		print("SubClassB._init()")

#=====
# 実行
#=====
func _ready():
	……
	var _subClassA = SubClassA.new() #-> SubClassA._init()
	print(_subClassA) #-> [RefCounted:-9223372012041272799]
	print(_subClassA is SubClassA) #-> true（＝SubClassA型）
	print(_subClassA is SuperClass) #-> true（＝SuperClass型）
	print(_subClassA.pSubA) #-> 派生クラスＡのプロパティ
	print(_subClassA.pSuper) #-> 基本クラスのプロパティ
	print(_subClassA.mSubA()) #-> 派生クラスＡのメソッド
	print(_subClassA.mSuper()) #-> 基本クラスのメソッド

	var _subClassB = SubClassB.new() #-> SubClassB._init()
	print(_subClassB) #-> [RefCounted:-9223372012024495730]
	print(_subClassB is SubClassB) #-> true（＝SubClassB型）
	print(_subClassB is SuperClass) #-> true（＝SuperClass型）
	print(_subClassB.pSubB) #-> 派生クラＢのプロパティ
	print(_subClassB.pSuper) #-> 基本クラスのプロパティ
	print(_subClassB.mSubB()) #-> 派生クラスＢのメソッド
	print(_subClassB.mSuper()) #-> 基本クラスのメソッド
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E5%9F%BA%E6%9C%AC%E3%82%AF%E3%83%A9%E3%82%B9%E3%81%A8%E6%B4%BE%E7%94%9F%E3%82%AF%E3%83%A9%E3%82%B9)]  
参考：[GODOT DOCS（**Inheritance**）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_basics.html?highlight=inheritance#inheritance)  
参考：[ファイルがクラス！](http://puggygame.blogspot.com/2018/03/gdscript.html)  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月05日  
更新日：2022年08月20日  
[[TOP](#TOP)]


<a name="名前空間"></a>
# <b>名前空間</b>

### 概要
他のディレクトリにある .gd ファイルモジュールを読み込んで活用します。.gd ファイルには再利用可能なコード（クラス）群を記述します。

### 例文
* res://Main.gd と同階層に japan ディレクトリがあり、その中に tokyo.gd が存在する場合

```gdscript
# res://japan/tokyo.gd
class Shinjuku:
	func _init():
		print("japan/tokyo/Shinjuku")

class Setagaya:
	func _init():
		print("japan/tokyo/Setagaya")
```

```gdscript
# /root/Main(Main.gd)（外部.gdファイルを利用する側）
extends Node3D
……
func _ready():
	……
	var _tokyo = preload("res://japan/tokyo.gd") # 外部.gdファイルの読み込み
	_tokyo.Shinjuku.new() #-> "japan/tokyo/Shinjuku"
	_tokyo.Setagaya.new() #-> "japan/tokyo/Setagaya"
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E5%90%8D%E5%89%8D%E7%A9%BA%E9%96%93)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月13日  
更新日：2022年08月14日  
[[TOP](#TOP)]


<a name="継承と委譲"></a>
# <b>継承と委譲</b>

### 概要
*  GoF デザインパターンの [Adapter パターン](http://bit.ly/2naab8x)等で利用される
* 継承の場合は **extends クラス名** を使い、委譲の場合は **クラス名.new()** を使ってオブジェクトを生成し、他のクラスの機能を利用する
* サンプルは「[クラスファイル](https://github.com/mubirou/HelloWorld/blob/master/languages/GDScript/GDScript_reference.md#%E3%82%AF%E3%83%A9%E3%82%B9%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%92%E4%BD%BF%E3%81%86%E6%96%B9%E6%B3%95)」を使用

### 👉 継承版

#### ClassA の定義
```gdscript
# res://ClassA.gd
class_name ClassA

func myMethod():
	print("ClassA.myMethod()")
```

#### ClassB（ClassA を継承）の定義
```gdscript
# res://ClassB.gd（この中身だけ委譲版と異なる）
class_name ClassB extends ClassA # ポイント
# extends 以降を別行にしても可能
```

#### 実行
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	………
	var _classB = ClassB.new()
	_classB.myMethod() #-> ClassA.myMethod()
```

### 👉 委譲版

#### ClassA の定義
```gdscript
# res://ClassA.gd
class_name ClassA

func myMethod():
	print("ClassA.myMethod()")
```

#### ClassB の定義
```gdscript
# res://ClassB.gd（この中身だけ継承版と異なる）
class_name ClassB

var _classA = ClassA.new() # ポイント

func myMethod():
	_classA.myMethod()
```

#### 実行
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	………
	var _classB = ClassB.new()
	_classB.myMethod() #-> ClassA.myMethod()
```

[[C# 版](https://bit.ly/3c58g0H)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月06日  
更新日：2022年08月20日  
[[TOP](#TOP)]


<a name="変数とスコープ"></a>
# <b>変数とスコープ</b>

### 変数の種類
1. [グローバル変数](#グローバル変数) 
1. [疑似プライベート変数](#疑似プライベート変数) 
1. [ローカル変数](#ローカル変数) 

<a name="グローバル変数"></a><a name="グローバル変数"></a>

### 👉 グローバル変数
1. [ファイルシステム]上で右クリック→[新規スクリプト]を選択
1. [パス]は "**res://Global.gd**" としコードを次の通りに記述  
    ```gdscript
    #res://Global.gd
    extends Node
    var someGlobal = 100
    ```
1. [プロジェクト]-[プロジェクト設定]-[Autoload（自動読み込み）]を選択
1. [パス]-[📁] から上記の **Global.gd** を選択し [追加]  
![image](https://github.com/mubirou/Godot/blob/main/jpg/202208131844.jpg)
1. 動作確認  
    ```gdscript
	# /root/Main(Main.gd)
	extends Node3D
	……
	func _ready():
		……
		print(Global.someGlobal) #-> 100（参照）
		Global.someGlobal = 200 # 変更
		print(Global.someGlobal) #-> 200（変更されている）
    ```
参考：[共有ファイル](https://bit.ly/3KbSj5v)  

<a name="疑似プライベート変数"></a>

### 👉 疑似プライベート変数

1. [クラス](#クラス)の定義
	```gdscript
	# res://MyClass.gd（クラスファイル）
	class_name MyClass

	# 擬似プライベート変数の定義（実際は単なるパブリック変数）
	var __propA = "いろは" # 変数名は__xxxにする（任意）

	# setter/getter（変数へのアクセスは[アクセサ]を利用する＝推奨）
	var propA:
		get: return __propA
		set(value): __propA = value
	```

1. 実行
	```gdscript
	# /root/Main(Main.gd)
	extends Node3D
	……
	func _ready():
		……
		var _myClass = MyClass.new()

		# 良い例（setter/getterを使ってアクセスする）
		print(_myClass.propA) #-> "いろは"（参照）
		_myClass.propA = "ABC" # 変更
		print(_myClass.propA) #-> "ABC"（変更されている）

		# 悪い例（外部から直接アクセスするべきではない）
		_myClass.__propA = "あいう" # 外部から直接変更
		print(_myClass.__propA) #-> "あいう"（変更できてしまう）
	```

<a name="ローカル変数"></a>

### 👉 ローカル変数
1. 関数内で宣言する場合（if 文等でも同様）  
    ※宣言したブロック内かつ、インデントが同じかより深い範囲内で有効
    ```gdscript
    # /root/Main(Main.gd)
	extends Node3D
	……
	func _ready():
		……
		myFunction1()
		myfunction2()
		#print(_local) # Error（アクセス不可）

	func myFunction1():
		var _local = "ローカル変数" # ローカル変数の宣言
		print(_local) #-> "ローカル変数"

	func myfunction2():
		#print(_local) # Error（アクセス不可）
		pass
    ```

1. クラスの関数内で宣言する場合
    ```gdscript
	# /root/Main(Main.gd)
	extends Node3D
	……
	class MyClass:
		var _public = "パブリック変数"
		func myMethod():
			var _local = "ローカル変数"
			print(_local)

	func _ready():
		……
		var _myClass = MyClass.new()
		_myClass.myMethod() #-> ローカル変数
		print(_myClass._public) #-> パブリック変数
		#print(_myClass._local) # アクセス不可
    ```

1. for 文内のループ変数
    ```gdscript
	for _i in range(6): #ローカル変数（_i）0～5
		print(_i) #-> 0,1,2,...,5
	#print(_i) # Error（for文外ではアクセス不可）
    ```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E5%A4%89%E6%95%B0%E3%81%A8%E3%82%B9%E3%82%B3%E3%83%BC%E3%83%97)]  
実行環境：Windows 10、Godot 4.0 alphba 14  
作成者：夢寐郎  
作成日：2022年01月08日  
更新日：2022年08月21日  
[[TOP](#TOP)]


<a name="アクセサ"></a>
# <b>アクセサ（getter / setter）</b>

### 読み書き可能なプロパティ
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
class Member:
	var __age = 19 # 疑似プライベート変数
	
	# setter/getter
	var age:
		get: return __age
		set(value): __age = value

# 実行
func _ready():
	……
	var _member = Member.new()
	print(_member.age) #-> 19
	_member.age = 20
	print(_member.age) #-> 20
```

### 読み取り専用のプロパティ
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
class Member:
	var __age = 19 # 疑似プライベート変数
	
	# setter/getter
	var age: 
		get: return __age

# 実行
func _ready():
	……
	var _member = Member.new()
	print(_member.age) #-> 19
	_member.age = 20 # 変更不可（エラーは出ない）
	print(_member.age) #-> 19
```

### 書き込み専用のプロパティ
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
class Member:
	var __age = 19 # 疑似プライベート変数
	
	# setter/getter
	var age: 
		set(value): __age = value

# 実行
func _ready():
	……
	var _member = Member.new()
	_member.age = 20
	print(_member.age) #-> null
	print(_member.__age) #-> 20（内部では変更されている）
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%82%A2%E3%82%AF%E3%82%BB%E3%82%B5-getter--setter)]  
実行環境：Windows 10、Godot 4.0 alpha 14    
作成者：夢寐郎  
作成日：2022年01月06日  
更新日：2022年08月18日 Godot 4.0 対応  
[[TOP](#TOP)]  


<a name="演算子"></a>
# <b>演算子</b>

### 算術演算子
```gdscript
# /root/Main(Main.gd)
extends Node3D

func _ready():
	print(3 + 2) #-> 5 (可算) 
	print(5 - 8) #-> -3 (減算)
	print(3 * 4) #-> 12 (乗算)
	print(1 + 2 * 3 - 4 / 2) #-> 5 (複雑な計算)
	print(63 % 60) #-> 3 (余剰)

	# 除算（注意が必要です）
	print(8 / 3) #-> 2(除算) ←整数同士の場合、余りは切り捨てられる
	print(8 / 3.0) #-> 2.66666666666667（小数点第14位までの値＝float型）

	#インクリメント（++）・デクリメント（--）は存在しないので以下で代用
	var _hoge = 0
	_hoge += 1
	print(_hoge) #-> 1
```

### その他の演算子
```gdscript
# /root/Main(Main.gd)
extends Node3D

func _ready():
	# 論理積
	print(true and true) #-> true
	print(true && true) #-> true

	# 論理和
	print(true or false) #-> true
	print(true || false) #-> true

	# 否定
	print(not true) #-> false
	print(! true) #-> false
 
	print(2 < 3) #-> true（比較/未満）
	print(2 <= 2) #-> true（比較/以下）
	print(1 == 1.0) #-> true（等号）
	print(1 != 1.0) #-> false（不等号）

	print(3 & 1) #-> 1（ビット積）
	print(3 | 1) #-> 3（ビット和）
	print(3 ^ 1) #-> 2（排他的ビット和）
	print(2 << 7) #-> 256（ビット･シフト）
	print(~3) #-> -4（ビット反転）
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E6%BC%94%E7%AE%97%E5%AD%90)]  
参考：[GODOT DOCS（**Operators**）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_basics.html?highlight=x.attribute#operators)  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月09日  
更新日：2022年08月20日  
[[TOP](#TOP)]


<a name="定数"></a>
# <b>定数</b>

### 通常の定数
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
const MY_NAME = "MUBIROU"
……
func _ready():
	……	
	print(MY_NAME) #-> MUBIROU
	MY_NAME = "ICHIRO" # Parser Error（変更不可）
```

### クラス定数（[静的変数](#静的変数・静的関数)）
```gdscript
# res://MyClass.gd（クラスファイル）
class_name MyClass

const MY_NAME = "MUBIROU" # クラス定数の定義

func _init():
	print(MY_NAME) #-> "MUBIROU"（クラス内でアクセス可）
```
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……	
	print(MyClass.MY_NAME) #-> MUBIROU（インスタンス生成せずにアクセス可）
	#MyClass.MY_NAME = "ICHIRO" # Error（変更不可）
	
	var _myClass = MyClass.new()
	print(_myClass.MY_NAME) #-> MUBIROU（インスタンスからもアクセス可）
	#_myClass.MY_NAME = "ICHIRO" # 変更不可
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E5%AE%9A%E6%95%B0)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月09日  
更新日：2022年08月21日  
[[TOP](#TOP)]


<a name="関数"></a>
# <b>関数</b>

### 関数の種類
1. [**パブリック関数**](#関数-1) 
1. [**疑似プライベート関数**](#関数-2) 
1. [**コンストラクタ**](#関数-3) 
1. [**_ready()、_process()、_physics_process() 関数**](#関数-4)
1. [**入力イベント**](#関数-5)
1. [**静的関数**](#静的関数)
1. [**デフォルト値付き引数**](#関数-6)

### 👉 基本構文
```gdscript
func 関数名(引数➀, 引数➁, ...):
	......
	[return 戻り値]
	[pass]（何もしない場合 pass を記述）
```
* [pass](https://godotengine.org/qa/19110/difference-between-pass-and-return) について  
Pythonのコードブロックは {} ではなくインデントを揃えることで見なします。しかしインデントを強制する文法の弱点として、インデントしたブロックは必ず１行以上の記述が必要になります。そこで「何もしない」という処理を意味する [pass](https://godotengine.org/qa/19110/difference-between-pass-and-return) 文が用意されています。
* サンプルコード
	```gdscript
	# /root/Main(Main.gd)
	extends Node3D
	……
	func _ready():
		……
		print(tashizan(1, 10)) #-> 55
		
	#print(tashizan(1, 10)) #-> Parser Error（ここでは実行できない）

	func tashizan(_start, _end):
		var _result = 0 #ローカル変数
		for i in range(_start, _end + 1):
			_result += i
		return _result
	```

### 👉 パブリック関数<a name="関数-1"></a>
* 例：○〜○までの値を足した合計を調べる
	```gdscript
	# res://MyClass.gd（クラスファイル）
	class_name MyClass

	func tashizan(_start, _end):
		var _result = 0 #ローカル変数
		for i in range(_start, _end + 1):
			_result += i
		return _result
	```
	```gdscript
	# /root/Main(Main.gd)
	extends Node3D
	……
	func _ready():
		……	
		var _myClass = MyClass.new()
		print(_myClass.tashizan(1, 10)) #-> 55
		print(_myClass.tashizan(1, 100)) #-> 5050
	```
[[関数TOP](#関数)]  

### 👉 疑似プライベート関数<a name="関数-2"></a>
* 実際は単なるパブリック関数
* アクセス修飾子が存在しないため、Python 風 に __メソッド名() と命名して外からアクセスしないようにする
	```gdscript
	# res://MyClass.gd（クラスファイル）
	class_name MyClass

	# 疑似プライベート関数（Python風に__〇〇とする）
	func __tashizan(_start, _end):
		var _result = 0 #ローカル変数
		for i in range(_start, _end + 1):
			_result += i
		return _result

	func _init():
		print(__tashizan(1, 10)) #-> 55
	```
	```gdscript
	# /root/Main(Main.gd)
	extends Node3D
	……
	func _ready():
		……	
		var _myClass = MyClass.new()
		print(_myClass.__tashizan(1, 10)) #-> 55（外からアクセスできてしまうが…）
	```
[[関数TOP](#関数)]  

### 👉 コンストラクタ<a name="関数-3"></a>

1. **「クラスファイル」を使う場合**
	```gdscript
	# res://MyClass.gd（クラスファイル）
	class_name MyClass

	func _init(arg):
		print("MyClass._init()")
		print(arg)
	```
	```gdscript
	# /root/Main(Main.gd)
	extends Node3D
	……
	func _ready():
		……
		var _myClass = MyClass.new("Hello")
	```

1. **ノードにアタッチしたスクリプトの場合**
	```gdscript
	# /root/Main(Main.gd)
	extends Node3D
	……
	func _init():
		print("Main._init()") # 先に実行される

	func _ready(): # 通常はこちらを使う
		……
		print("Main._ready()")
	```
	💡 [.gd ファイルがクラス！](http://puggygame.blogspot.com/2018/03/gdscript.html) であるためノードにアタッチしたスクリプトもクラスであると言えます。そのため [class_name](#クラス) を記述することで外部からアクセスが可能です。  
参考：[GODOT DOCS（**Class constructor**）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_basics.html#class-constructor)  
[[関数TOP](#関数)]  

### 👉 _ready()、_process()、_physics_process() 関数<a name="関数-4"></a>
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	_interface = XRServer.find_interface("OpenXR")
	if _interface and _interface.is_initialized():
		var _viewport : Viewport = get_viewport()
		_viewport.use_xr = true
		
func _process(_delta): # 繰り返し実行される
	print("process: " + str(Time.get_unix_time_from_system()))

func _physics_process(_delta): # 物理ステップの前に安定して実行される(初期値60fps)
	print("physics_process: " + str(Time.get_unix_time_from_system()))
```
参考：[GODOT DOCS（**Godot notifications**）](https://docs.godotengine.org/en/latest/tutorials/best_practices/godot_notifications.html?highlight=_physics_process#godot-notifications)  
[[関数TOP](#関数)]  


### 👉 入力イベント<a name="関数-5"></a>

参照 ⇒ [**VRコントローラーの入力イベント**](https://bit.ly/3wg7QeH)  
参考：[GODOT DOCS（**Connecting a signal**）](https://bit.ly/3PG7YLF)  


### 👉 静的関数<a name="静的関数"></a>
* [pow()](https://bit.ly/3K9rU8i) の代替例（車輪の再発明）
```gdscript
# res://MyMath.gd（クラスファイル）
class_name MyMath

static func Pow(arg1, arg2): # 慣例的に大文字で始める
	if arg2 == 0: return 1 # 0乗対策
	var _result = arg1
	for i in range(1, arg2):
		_result *= arg1
	return _result
```
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready(): # 通常はこちらを使う
	……
	print(MyMath.Pow(2,3)) #-> 8
	
	var _myMath = MyMath.new()
	print(_myMath.Pow(2,4)) #-> 16（インスタンスからも実行可）
```
参考：[GODOT DOCS（**Static functions**）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_basics.html#static-functions)  

[[関数TOP](#関数)]  

### 👉 デフォルト値付き引数<a name="関数-6"></a>
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready(): # 通常はこちらを使う
	……
	Hello() #-> Hello!（引数を指定しないと初期値で処理）
	Hello("ja") #-> こんにちは!（引数を指定した場合）
	
func Hello(arg = "en"):
	if arg == "en":
		print("Hello!")
	elif arg == "ja":
		print("こんにちは!")
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%83%A1%E3%82%BD%E3%83%83%E3%83%89)]  
参考：[GODOT DOCS（**Functions**）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_basics.html#functions)  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月15日  
更新日：2022年08月21日  
[[関数TOP](#関数)]  
[[TOP](#TOP)]


<a name="匿名関数"></a>
# <b>匿名関数</b>

```gdscript
# /root/Main(Main.gd)
……
var _hello : Callable
var _american : Callable
var _japanese : Callable
var _chinese : Callable

func _ready():
	……
	_american = func(_name): # 匿名関数➀
		print(_name + "," + "Hello!")

	_japanese = func(_name): # 匿名関数➁
		print(_name + "、" + "こんにちは!")
	
	_chinese = func(_name): # 匿名関数➂
		print(_name + "," + "你好!")
	
	_hello = _american #変数に匿名関数を代入
	_hello.call("TARO") #-> "TARO,Hello!"
	_hello = _japanese # 匿名関数の入替え
	_hello.call("太郎") #-> "太郎、こんにちは!"
	_hello = _chinese # 匿名関数の入替え
	_hello.call("太郎") #-> "太郎,你好!"
```

参考：[GODOT DOCS（**Callable**）](https://docs.godotengine.org/en/latest/classes/class_callable.html?highlight=Callable#callable)  
実行環境：Windows 10、Godot Engine 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年08月14日  
[[TOP](#TOP)]


<a name="静的変数・静的関数"></a>
# <b>静的変数・静的関数</b>

* 静的変数 ⇒ [定数](#定数)
* 静的関数 ⇒ [関数（静的関数）](#静的関数)

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E9%9D%99%E7%9A%84%E3%83%A1%E3%83%B3%E3%83%90static)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月15日  
更新日：2022年08月21日  
[[TOP](#TOP)]


<a name="if文"></a>
# <b>if 文</b>

### 基本構文
* trueと評価される可能性が高い順に並べるとif文を早く抜け出せる可能性が高い
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _age = 55
	if _age <= 20:
		print("20歳以下")
	elif _age <= 40: #「else if」でも「elseif」でもない（要注意）
		print("21〜40歳")
	elif _age <= 60:
		print("41〜60歳") #これが出力される
	else:
		print("61歳以上")
```

* 注意：条件式の判断記述について
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	if null: # '' "" []も同じfalseとして判断
		print("A")
	else:
		print("B") #こちらが実行される

	if "あ": # 中身が何かあればtrueとして判断
		print("A") #こちらが実行される
	else:
		print("B")
```

### 論理積（and または &&）
1. 論理演算子（and または &&）を使う方法
    ```gdscript
    if 条件式➀ and 条件➁:
        処理A ←条件式➀かつ条件式➁の両方がTrueの場合に実行
    else:
        処理B
    ```

1. ifのネストを使う方法
    ```gdscript
    if 条件式➀:
        if 条件➁:
            処理A ←条件式➀かつ条件式➁の両方がTrueの場合に実行
        else:
            処理B
    else:
        処理B
    ```

### 論理和（or または ||）
1. 論理演算子（or または ||）を使う方法
    ```gdscript
    if 条件式➀ or 条件➁:
        処理A ←条件式➀または条件式➁の両方がTrueの場合に実行
    else:
        処理B
    ```

1. ifのネストを使う方法
    ```gdscript
    if 条件式➀:
        処理A ←条件式➀がTrueの場合に実行
    elif 条件➁:
        処理A ←条件式②がTrueの場合に実行
    else:
        処理B
    ```

### 排他的論理和（XOR）
* GDScriptでは ^ 演算子は使えない
* 「&& は and」「|| は or」「! は not」でも可  
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _a = false
	var _b = false
	if (_a || _b) && !(_a && _b):
		print("どちらか一方だけtrue（false）です")
	else:
		print("両方共にtrueかfalseです")
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#if-%E6%96%87)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月08日  
更新日：2022年08月14日  
[[TOP](#TOP)]


<a name="三項演算子"></a>
# <b>三項演算子</b>

### 構文
* GDScript の三項演算子は [Pythonと同様](https://github.com/mubirou/HelloWorld/blob/master/languages/Python/Python_reference.md#%E4%B8%89%E9%A0%85%E6%BC%94%E7%AE%97%E5%AD%90) if 文を使った独特のものです
```gdscript
変数 = (True時の返り値) if (比較式) else (False時の返り値)
```

### 例文
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _age = 55
	var _result = "現役" if (_age < 60) else "退職"
	print(_result)
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E4%B8%89%E9%A0%85%E6%BC%94%E7%AE%97%E5%AD%90)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月09日  
更新日：2022年08月14日  
[[TOP](#TOP)]


<a name="match文"></a>
# <b>match ≒ switch 文</b>

### 判別式が bool 値ではない場合
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _name = "TARO"
	match _name:
		"TARO":
			print("父") # これが出力される
		"HANAKO":
			print("母")
		"ICHIRO":
			print("長男")
		"JIRO":
			print("次男")
		_:
			print("家族以外")
```

### ⚠ 注意➀：判別式に bool 型が使えない
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _age = 55
	match true:
		_age < 20: # Error（比較演算子を使った条件式は不可）
			print("未成年")
		_:
			print("成人")
```

### ⚠ 注意➁：フォロースルーの動作
* 以下の場合 "A" "C" が出力される
```gdscript
#Main.gd
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _value = "A"
	match _value:
		"A":
			print("A")
			continue
		"B":
			print("B")
			continue
		_:
			print("C")
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#switch-%E6%96%87)]  
参考：[GODOT DOCS（**match**）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_basics.html?highlight=%22in%20range%22#match)  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2021年01月09日  
更新日：2021年08月14日  
[[TOP](#TOP)]


<a name="for文"></a>
# <b>for 文</b>

### 基本構文
```gdscript
for 変数 in range(開始, 終了):
    繰り返す処理
```

### 基本例文
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……	
	for i in range(0, 10):
		print(i) #-> 0,1,2,3,4,5,6,7,8,9
	#print(i) # Error（for文の外ではiは無効）
```

### for 文のネスト
* ループ制御変数には i, j, k が使われる
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……	
	for i in range(1, 6):
		for j in range(1, 6):
			print("x" + str(i) + "y" + str(j)) #-> x1y1, x1y2, …, x5y4, x5y5
```

### continue 文
* ループカウンタを○つずつアップする
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……	
	for i in range(0,50):
		if i % 5: # 5つずつアップする場合…
			continue # 以降処理せずfor文のブロックの先頭に戻って再度繰返す
		print(i) #-> 0, 5, 10, 15, 20, 25, 30, 35, 40, 45
```

### 無限ループと break 文
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _count = 0
	for i in range(0, 99999999999999999): # ほぼ無限ループ（厳密な無限にはwhile文を使用）
		_count += 1
		if (_count > 100):
			break #100 を超えたらループを抜け出す
		print(_count) #-> 1, 2, ...., 99, 100
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#for-%E6%96%87)]  
参考：[GODOT DOCS（**for**）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_basics.html?highlight=%22in%20range%22#for)  
実行環境：Windows 10、Godot 4.0 alpha 14    
作成者：夢寐郎  
作成日：2022年01月09日  
更新日：2022年08月14日  
[[TOP](#TOP)]


<a name="while文"></a>
# <b>while 文</b>
* 他の多くの言語にある do...while 文はない

```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _i = 0
	while _i < 10:
		print(_i) #-> 0,1,2,3,4,5,6,7,8,9
		_i += 1
	print(_i) #-> 10（while文の外でも変数はまだ有効）
```

### while 文と break 文
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _count = 0
	while true: # ループ判別式をtrueにすると無限ループに!
		_count += 1
		if _count > 100:
			break # ループを終了
		print(_count) #-> 1,2,....,99,100（1〜100までを出力）
	print("while文終了") # while文の外
```

### while 文と continue 文（3の倍数を出力）
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _i = 1
	while _i <= 20:
		if (_i % 3) != 0: # 3で割って余りが0ではない（＝3の倍数ではない）場合
			_i += 1
			continue # while文の残処理をスキップしてwhile文の次の反復を開始する
		print(_i) #-> 3,6,9,12,15,18（3の倍数を出力）
		_i += 1
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#while-%E6%96%87)]  
参考：[GODOT DOCS（**while**）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_basics.html?highlight=%22in%20range%22#while)  
実行環境：Windows 10、Godot Engine 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月24日  
更新日：2022年08月14日  
[[TOP](#TOP)]


<a name="配列"></a>
# <b>配列</b>

1. [作成](#配列作成)
1. [要素の数](#配列要素の数)
1. [抽出](#配列抽出)
1. [追加（最後）](#配列追加（最後）)
1. [追加（指定位置）](#配列追加（指定位置）)
1. [更新（指定位置）](#配列更新（指定位置）)
1. [削除（指定の要素）](#配列削除（指定の要素）)
1. [削除（指定位置）](#配列削除（指定位置）)
1. [検索（ヒットしたか否か）](#配列検索（ヒットしたか否か）)
1. [検索（ヒット数）](#配列検索（ヒット数）)
1. [並べ替え（反転）](#配列並べ替え（反転）)
1. [並べ替え（ソート）](#配列並べ替え（ソート）)
1. [シャッフル](#配列シャッフル)
1. [結合](#配列結合)
1. [複製](#配列複製)
1. [文字列→配列](#配列文字列→配列)
1. [全要素を取り出す](#配列全要素を取り出す)
1. [フィルタをかける](#フィルタをかける)

<a name="配列作成"></a> 

### 👉 作成
```gdscript
var _array1 = [] # 空の配列を作成
print(_array1) #-> []

var _array2 = ["A", "B", "C"]
print(_array2) #-> ["A", "B", "C"]

var _array3 = [["A", "あ"], ["I", "い"]] # 配列のネスト
print(_array3) #-> [["A", "あ"], ["I", "い"]]

var _array4 = range(0, 10)
print(_array4) #-> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<a name="配列要素の数"></a>

### 👉 要素の数
```gdscript
var _array = [0,1,2,3,4,5,6,7,8,9]
print(_array.size()) #-> 10
```

<a name="配列抽出"></a>

### 👉 抽出
```gdscript
var _array = [0,1,2,3,4,5,6,7,8,9]

# 先頭の抽出
print(_array.front()) #-> 0
print(_array[0]) #-> 0

# 最後尾の抽出
print(_array.back()) #-> 9
print(_array[-1]) #-> 9
print(_array[_array.size() - 1]) #-> 9

# 指定位置の抽出
print(_array[5]) #-> 5（インデックス5番目）
```

<a name="配列追加（最後）"></a>

### 👉 追加（最後）
```gdscript
var _array = []
_array.append("mubirou") # String型の追加
_array.append(100) # int型の追加
print(_array) #-> ["mubirou", 100]（混在可能）
```

<a name="配列追加（指定位置）"></a>

### 👉 追加（指定位置）
```gdscript
var _array = ["A", "B"]
_array.insert(0, "C") # インデックス0（先頭）に追加
print(_array) #-> ["C", "A", "B"]
```

<a name="配列更新（指定位置）"></a>

### 👉 更新（指定位置）
```gdscript
var _array = ["A", "B", "C"]

_array[0] = null # インデックス0（先頭）を更新
print(_array) #-> [null, "B", "C"]

_array[-1] = "D" # 後ろから1番目を更新
print(_array) #-> [null, "B", "D"]
```

<a name="配列削除（指定の要素）"></a>

### 👉 削除（指定の要素）
```gdscript
var _array = ["A", "B", "C"]
_array.erase("A") # 最初に見つかった指定の要素を削除
print(_array) #-> ["B", "C"]
```

<a name="配列削除（指定位置）"></a>

### 👉 削除（指定位置）
```gdscript
var _array = ["A", "B", "C"]
_array.remove_at(1) # インデックス1の要素を削除
print(_array) #-> ["A", "C"]
```

<a name="配列検索（ヒットしたか否か）"></a>

### 👉 検索（ヒットしたか否か）
```gdscript
var _array = ["A", "B", "C", "D", "E"]
print("E" in _array) #-> true
print("F" in _array) #-> false
```

<a name="配列検索（ヒット数）"></a>

### 👉 検索（ヒット数）
```gdscript
var _array = ["A", "C", "B", "C", "A", "C"]
print(_array.count("C")) #-> 3
print(_array.count("D")) #-> 0
```

<a name="配列並べ替え（反転）"></a>

### 👉 並べ替え（反転）
```gdscript
var _array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
_array.reverse()
print(_array) #-> [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

<a name="配列並べ替え（ソート）"></a>

### 👉 並べ替え（ソート）
```gdscript
var _array = [3, 6, 2, 8, 4, 1, 9, 0, 5, 7]
_array.sort()
print(_array) #-> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<a name="配列シャッフル"></a>

### 👉 シャッフル
```gdscript
var _array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
_array.shuffle()
print(_array) #-> [5, 7, 8, 4, 6, 1, 2, 3, 0, 9]（毎回異なる）
``` 

<a name="配列結合"></a>

### 👉 結合
```gdscript
var _array1 = ["A","B","C"]
var _array2 = ["D","E","F"]
_array1 += _array2
print(_array1) #-> ["A", "B", "C", "D", "E", "F"]
```

<a name="配列複製"></a>

### 👉 複製
```gdscript
var _origin = ["A","B"]
var _copy = _origin.duplicate()
_copy[0] = "C" #値を変更してみる
print(_origin) #-> ["A", "B"]（参照ではないことが判る）
print(_copy) #-> ["C", "B"]
```

<a name="配列文字列→配列"></a>

### 👉 文字列→配列
```gdscript
var _string = "A,B,C"
var _array = _string.rsplit (",") # カンマ区切りで分割してリスト化
print(_array) #-> ["A", "B", "C"]
```

<a name="配列全要素を取り出す"></a>

### 👉 全要素を取り出す
```gdscript
var _count = 0 # インデックス番号取得用（オプション）
for _tmp in ["A","B","C","D","E"]:
	print(str(_count) + ":" + _tmp) 
	#-> 0:A → 1:B → 2:C → 3:D → 4:E
	_count += 1
```

<a name="フィルタをかける"></a>

### 👉 フィルタをかける  
GDScript 2.0 の新機能（ラムダ式＝匿名関数)を利用 
```gdscript
var _array = [5, 7, 8, 4, 6, 1, 2, 3, 0, 9]
print(_array.filter(func(x): return x < 5)) #-> [4, 1, 2, 3, 0]
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E5%8B%95%E7%9A%84%E9%85%8D%E5%88%97list)]  
参考：[GODOT DOCS（**Array**）](https://docs.godotengine.org/en/latest/classes/class_array.html?highlight=Array#array)  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月25日  
更新日：2022年08月15日 Godot 4.0 対応  
[[TOP](#TOP)]


<a name="連想配列（辞書）"></a>
# <b>連想配列（辞書）</b>

### 👉 作成
```gdscript
var 変数名 = {"キー➀": 値➀, "キー➁": 値➁}
```

### 👉 追加･更新
* 構文
```gdscript
辞書["キー"] = 値
```
* 例文
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _dict = {"A": "あ", "I": "い"}
	_dict["U"] = "う" # 追加（存在する場合は更新）
	print(_dict) #-> {"A":"あ", "I":"い", "U":"う"}
```

### 👉 取得
* 構文
```gdscript
辞書["キー"]
辞書.get("キー", [キーが無い場合の初期値])
```
* 例文
```gdscript
var _dict = {"A": "あ", "I": "い", "U": "う"}
print(_dict["A"]) #-> あ
print(_dict.get("A", null)) #-> あ（第2引数は省略可）
```

### 👉 削除
* 構文
```gdscript
辞書.erase("キー") # 任意のキーのペア
辞書.clear() # 全てのキーのペア
```
* 例文
```gdscript
var _dict = {"A": "あ", "I": "い", "U": "う"}
_dict.erase("A")
print(_dict) #-> {"I":"い", "U":"う"}
```

### 👉 キーの検索
* 構文
```gdscript
"キー" in 辞書
```
* 例文
```gdscript
var _dict = {"A": "あ", "I": "い", "U": "う"}
print("A" in _dict) #-> true（任意のキーが無いとfalse）
```

### 👉 要素数
* 構文
```gdscript
辞書.size()
len(辞書)
```
* 例文
```gdscript
var _dict = {"A": "あ", "I": "い", "U": "う"}
print(_dict.size()) #-> 3
print(len(_dict)) #-> 3
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E9%80%A3%E6%83%B3%E9%85%8D%E5%88%97dictionary)]  
参考：[GODOT DOCS（**Dictionary**）](https://docs.godotengine.org/en/latest/classes/class_dictionary.html?highlight=dictionary#dictionary)  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月27日  
更新日：2022年08月15日  
[[TOP](#TOP)]


<a name="self"></a>
# <b>self</b> ≒ this

self は現在のクラスインスタンスを参照するのは同じだが [Python の self](https://github.com/mubirou/HelloWorld/blob/master/languages/Python/Python_reference.md#self--this) ほど重要ではない
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
class MyClass:
	var _p #= null # __p（擬似プライベート変数）にすれば心配ないが…
	
	func _init(_p): # 引数がインスタンス名を同じ場合…
		print(_p) #-> 500
		print(self._p) #-> null
		self._p = _p # この場合は self が必須（ポイント！）
		print(self) #-> [RefCounted:-9223372012007718366]（※同じ）
		self.myMethod() #-> 500（selfは省略可能）

	func myMethod():
		print(_p)

func _ready():
	……
	var _myClass = MyClass.new(500)
	print(_myClass) #-> [RefCounted:-9223372012007718366]（※同じ）
	_myClass.myMethod() #-> 500
```

### 📝 ノードにアタッチしたスクリプト内の **self** について  
* 階層構造（サンプル）  

  **Main**（Node3D）![image](https://github.com/mubirou/HelloWorld/blob/master/languages/GDScript/png/script.png)（**Main.gd**）  
　├ XROrigin3D  
　├ **Box**（MeshInstance3D）![image](https://github.com/mubirou/HelloWorld/blob/master/languages/GDScript/png/script.png)（**Box.gd**）  
　└ **Sphere**（MeshInstance3D）![image](https://github.com/mubirou/HelloWorld/blob/master/languages/GDScript/png/script.png)（**Sphere.gd**）  

* **Main** にアタッチしたスクリプト（**Main.gd**）
	```gdscript
	# /root/Main(Main.gd)
	extends Node3D
	……
	func _ready():
		……
		# 全て同じ値
		print(self) #-> Main:[Node3D:2503160XXXX]
		print(get_parent().get_node("Main"))
		print(get_node("/root/Main"))
		print(get_tree().get_root().get_node("Main"))
	```
* **Box** にアタッチしたスクリプト（**Box.gd**）
	```gdscript
	# /root/Main/Box(Box.gd)
	extends MeshInstance3D

	func _ready():
		# 全て同じ値
		print(self) #-> Box:[MeshInstance3D:2509871XXXX]
		print(get_parent().get_node("Box"))
		print(get_node("/root/Main/Box"))
		print(get_tree().get_root().get_node("Main").get_node("Box"))
	```
* **Sphere** にアタッチしたスクリプト（**Sphere.gd**）
	```gdscript
	# /root/Main/Sphere(Sphere.gd)
	extends MeshInstance3D

	func _ready():
		# 全て同じ値
		print(self) #-> Sphere:[MeshInstance3D:2511549XXXX]
		print(get_parent().get_node("Sphere"))
		print(get_node("/root/Main/Sphere"))
		print(get_tree().get_root().get_node("Main").get_node("Sphere"))
	```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#this)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年01月28日  
更新日：2022年08月22日「ノードにアタッチしたスクリプト内の self について」追加  
[[TOP](#TOP)]


<a name="文字列の操作"></a>
# <b>文字列の操作</b>

### 👉 String オブジェクトの作成
```gdscript
var _string1 = String("あいうえお")
var _string2 = "あいうえお"
var _string3 = 'あいうえお' # "〇〇"と同じ
var _string4 = "１行目\n２行目"
```

### 👉 長さを調べる
```gdscript
var _string1 = "ABCDE"
print(_string1.length()) #-> 5

var _string2 = "あいうえお"
print(_string2.length()) #-> 5（全角文字も１字扱い）
```

### 👉 文字列の連結
* 加算演算子を使う場合
```gdscript
var _address1 = "東京都"
var _address2 = "新宿区"
print(_address1 + _address2) #-> 東京都新宿区
```
* フォーマット文字列を使う場合
```gdscript
var _address = "東京都%s"
print(_address % "新宿区") #-> "東京都新宿区"
```
参考：[GODOT DOCS（**GDScript format strings**）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_format_string.html?highlight=gdscript-format-strings#gdscript-format-strings)（フォーマット文字列）  

### 👉 一部分を取得
```gdscript
var _string = "0123456789"
print(_string[4]) #-> "4"
print(_string.substr(4)) #-> "456789"
print(_string.substr(4, 3)) #-> "456"
```

### 👉 一部分を削除
```gdscript
var _string = "ABCDCBA"
print(_string.lstrip("A")) #-> "BCDCBA"（左端から1つ削除）
print(_string.rstrip("A")) #-> "ABCDCB"（右端から1つ削除）
print(_string) #-> "ABCDCBA"（元は変更なし）
```

### 👉 置換
```gdscript
var _string = "2022年8月15日"
print(_string.replace("2022年", "令和4年")) #-> "令和4年8月15日
```

### 👉 検索
```gdscript
var _string = "ABCDEFG-ABCDEFG"
if ("CD" in _string) : # 見つかった（true）場合…
	print(_string.find("CD")) #-> 2（左から検索）
	print(_string.rfind("CD")) #-> 10（右から検索）
```

### 👉 文字列→配列
```gdscript
var _string = "A,B,C" # 「,」区切りの文字列
var _list = _string.split(',') # 「,」区切りで分割して配列化
print(_list) #-> ["A", "B", "C"]
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E6%96%87%E5%AD%97%E5%88%97%E3%81%AE%E6%93%8D%E4%BD%9C)]  
参考：[GODOT DOCS（**String**）](https://docs.godotengine.org/en/latest/classes/class_string.html?highlight=String#string)  
実行環境：Windows 10、Godot Engine 3.4.2  
作成者：夢寐郎  
作成日：2022年02月05日  
更新日：2022年08月15日  
[[TOP](#TOP)]


<a name="正規表現"></a>
# <b>正規表現</b>

### 📝 概要
* 正規表現は、URL、パスワード、メールアドレス等、特定の文字パターンを抽出するのに利用
* 正規表現の基本文法は、特定のプログラミング言語に依存しない
* GDScript には以下のサンプル以外にも多くの正規表現の機能が用意されている

### 👉 検索
```gdscript
var _string = "吉田松蔭,高杉晋作,久坂玄瑞,吉田稔麿,伊藤博文"
var _regex = RegEx.new()
_regex.compile("吉田")
var _result = _regex.search(_string)
if _result == null:
	print("吉田は含まれていません")
else:
	print("吉田は含まれています")
```

### 👉 置換
```gdscript
var _string = "吉田松蔭,高杉晋作,久坂玄瑞,吉田稔麿,伊藤博文"
var _regex = RegEx.new()
_regex.compile("吉田")
print(_regex.sub(_string, "よしだ"))
#-> "よしだ松蔭,高杉晋作,久坂玄瑞,吉田稔麿,伊藤博文"
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E6%AD%A3%E8%A6%8F%E8%A1%A8%E7%8F%BE)]  
参考：[GODOT DOCS（**RegEx**）](https://docs.godotengine.org/en/latest/classes/class_regex.html?highlight=RegEx#regex)  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年02月05日  
更新日：2022年08月15日  
[[TOP](#TOP)]


<a name="抽象クラス"></a>
# <b>抽象クラス</b>

### 概要
* GDScript には [interface](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%82%A4%E3%83%B3%E3%82%BF%E3%83%BC%E3%83%95%E3%82%A7%E3%83%BC%E3%82%B9) や [abstract](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E6%8A%BD%E8%B1%A1%E3%82%AF%E3%83%A9%E3%82%B9abstract) キーワードは存在しない
* 以下のサンプルでは疑似的に継承と例外を使って抽象クラスを実現

```gdscript
# /root/Main(Main.gd)
extends Node3D
……
# 擬似抽象クラスの定義（実際には単なる基本クラス）
class AbstractClass:
	func common(): # 共通の関数
		print("共通の関数")

	func abstractFunction(): # 擬似抽象関数の宣言（実際は単なる関数）
		assert(false, "Error: 派生クラスで実装する必要があります") # 例外処理

# 派生クラス
class SubClass extends AbstractClass: #擬似抽象クラスを継承
	func abstractFunction(): # オーバーライドして実際の処理を記述
		print("派生クラスでオーバーライドした抽象関数") # 実際の処理

# 実行
func _ready():
	……
	var _subClass = SubClass.new()
	_subClass.common() #-> "共通の関数"
	_subClass.abstractFunction() #-> "派生クラスでオーバーライドした抽象関数"
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E6%8A%BD%E8%B1%A1%E3%82%AF%E3%83%A9%E3%82%B9abstract)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年02月06日  
更新日：2022年08月15日  
[[TOP](#TOP)]


<a name="superキーワード"></a>
# <b>super キーワード</b>
旧「 [**.**（ドット）](https://docs.godotengine.org/ja/stable/tutorials/scripting/gdscript/gdscript_basics.html?highlight=super#inheritance)」の新しい書き方  

```gdscript
# /root/Main(Main.gd)
extends Node3D
……

# 基本（基底）クラス
class SuperClass:
	func _init(arg):
		print("SuperClass._init()" + " : " + str(arg))

	func hoge(arg): # 派生クラスでオーバーライドされる
		print("SuperClass.hoge(): " + arg)

# 派生クラス
class SubClass extends SuperClass:
	func _init():
		print("SubClass._init()")
		super(100) # 基本クラスのコンストラクタを呼び出す
	
	func hoge(arg): # 基本クラスの関数をオーバーライド
		print("SubClass.hoge(): " + arg)
		super.hoge("Hello2") # 基本クラスの関数を呼び出す

# 実行
func _ready():
	……		
	var _subClass = SubClass.new()
	_subClass.hoge("Hello1") 
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#base-%E3%82%AD%E3%83%BC%E3%83%AF%E3%83%BC%E3%83%89)]  
参考：[GODOT DOCS（**Class constructor**）](https://docs.godotengine.org/en/latest/tutorials/scripting/gdscript/gdscript_basics.html?highlight=super#class-constructor)  
実行環境：Windows 10、Godot Engine 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年02月04日  
更新日：2022年08月14日  
[[TOP](#TOP)]


<a name="オーバーライド"></a>
# <b>オーバーライド</b>

### 概要
* 基本クラスで定義したメソッドを派生クラスで再定義することをオーバーライドと呼ぶ
* GDScript には [override](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%82%AA%E3%83%BC%E3%83%90%E3%83%BC%E3%83%A9%E3%82%A4%E3%83%89) キーワードはない
* 派生クラスから基本クラスのメソッドを呼び出したい場合は [**super.関数名()**](#superキーワード) を使う

```gdscript
# /root/Main(Main.gd)
extends Node3D
……
# 基本クラス
class SuperClass:
	func myFunction(): # 派生クラスでオーバーライドされる
		print("基本クラスのmyFunction()")

# 派生クラス
class SubClass extends SuperClass: #擬似抽象クラスを継承
	func myFunction(): # 基本クラスの関数をオーバーライドする
		print("派生クラスのmyFunction()")
		super.myFunction() # 基本クラスのmyFunction()を呼出す場合

# 実行
func _ready():
	……
	var _subClass = SubClass.new()
	_subClass.myFunction()
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%82%AA%E3%83%BC%E3%83%90%E3%83%BC%E3%83%A9%E3%82%A4%E3%83%89)]  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年02月06日  
更新日：2022年08月15日  
[[TOP](#TOP)]


<a name="202207130930"></a>
# <b>カスタムイベント</b>

```gdscript
extends Node3D

# カスタムクラス 
class MyGame:
	signal gameover # イベント名の定義

	var __energy = 100 # 疑似プライベート変数

	func fight():
		__energy -= 20
		if (__energy <= 0):
			emit_signal("gameover") # イベント発生

func _ready(): # 実行
	var _robot = MyGame.new()
	_robot.connect("gameover", gameoverHandler) # ≒addEventListener
	_robot.fight()
	_robot.fight()
	_robot.fight()
	_robot.fight()
	_robot.fight() #-> GAMEOVER

func gameoverHandler(): # 前方定義でなくてもよい
	print("GAMEOVER")
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%A0%E3%82%A4%E3%83%99%E3%83%B3%E3%83%88)]  
実行環境：Windows 10、Godot 4.0 alpha 11  
作成者：夢寐郎  
作成日：2022年01月05日  
更新日：2022年07月13日  Godot 4.0 対応  
[[TOP](#TOP)]


<a name="数学関数"></a>
# <b>数学関数</b>

### abs() : 絶対値
```gdscript
print(abs(100)) #-> 100
print(abs(-100)) #-> 100
```

### atan2() : アークタンジェント2
* 2つの値のアークタンジェント（逆タンジェント）
* X、Y 座標の角度をラジアン（rad）単位で返す
* Π ラジアン（3.141592…）は180°
```gdscript
var _disX = sqrt(3) # √3のこと
var _disY = 1
print(atan2(_disY, _disX)) #-> 0.5235987755983（弧度法）
print(180 * atan2(_disY, _disX) / PI) #-> 30（度数法）
```

### ceil() : 切り上げ
```gdscript
print(ceil(1.001)) #-> 2
print(ceil(1.999)) #-> 2
```

### cos() : コサイン（余弦）
```gdscript
print(cos(0)) #-> 1（0°）
print(cos(PI / 2)) #-> 0（90°）
print(cos(PI)) #-> -1（180°）
print(cos(PI * 3 / 2)) #-> -0（270°）←要注意
print(cos(PI * 2)) #-> 1（360°）
```

### floor() : 切り捨て
```gdscript
print(floor(1.001)) #-> 1
print(floor(1.999)) #-> 1
```

### max() : 比較（最大値）
```gdscript
print(max(5.01, -10)) #-> 5.01（2つの数値の比較）
```

### min() : 比較（最小値）
```gdscript
print(min(5.01, -10)) #-> -10（2つの数値の比較）
```

### PI : 円周率
```gdscript
print(PI) #-> 3.14159265358979
print(PI == 3.14159265358979) #-> False
```

### pow() : 累乗（べき乗）
```gdscript
print(pow(2, 0)) #-> 1（2の0乗）
print(pow(2, 8)) #-> 256（2の8乗）
```

### round() : 四捨五入
```gdscript
print(round(1.499)) #-> 1
print(round(1.500)) #-> 2
```

### sin() : サイン（正弦）
```gdscript
print(sin(0)) #-> 0（0°）
print(sin(PI / 2)) #-> 1（90°）
print(sin(PI)) #-> 0（180°）
print(sin(PI * 3 / 2)) #-> -1（270°）
print(sin(PI * 2)) #-> -0（360°）
print(sin(PI * 2) == 0) #-> false（要注意）
```

### sqrt() : 平方根（√XXX）
```gdscript
print(sqrt(2)) #-> 1.4142135623731（一夜一夜にひとみごろ）
print(sqrt(3)) #-> 1.73205080756888（人並みに奢れや）
print(sqrt(4)) #-> 2
print(sqrt(5)) #-> 2.23606797749979（富士山麓オウム鳴く）
print(sqrt(6)) #-> 2.44948974278318（二夜シクシク）
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E6%95%B0%E5%AD%A6%E9%96%A2%E6%95%B0math)]  
実行環境：Windows 10、Godot 4.0 alpha 14   
作成者：夢寐郎  
作成日：2022年01月10日  
更新日：2022年08月14日  
[[TOP](#TOP)]


<a name="乱数"></a>
# <b>乱数</b>

### 0.0〜1.0未満
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……	
	var _random = RandomNumberGenerator.new()
	_random.randomize() # シード値の初期化（任意）
	print(_random.randf()) #-> 0.18828691542149（0.0〜1.0以下）
```
（注意）**.randomize()** を実行しないと毎回結果が同じになる（＝同じシード値を使用しているため）

### 最小値〜最大値（float型）
```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _random = RandomNumberGenerator.new()
	_random.randomize() # シード値の初期化（任意）
	print(_random.randf_range(0, 100)) #-> 88.5496139526367（0.0〜100.0以下）
```
（注意）**.randomize()** を実行しないと毎回結果が同じになる（＝同じシード値を使用しているため）


### 最小値〜最大値（int型）
```gdscript
# /root/Main(Main.gd)
extends Node3D

var _interface:XRInterface

func _ready():
	_interface = XRServer.find_interface("OpenXR")
	if _interface and _interface.is_initialized():
		var _viewport : Viewport = get_viewport()
		_viewport.use_xr = true
	
	var _i0=0; var _i1=0; var _i2=0; var _i3=0; var _i4=0
	var _i5=0; var _i6=0; var _i7=0; var _i8=0; var _i9=0

	var _random = RandomNumberGenerator.new()
	_random.randomize() # シード値の初期化（任意）

	for i in range(0, 100000): # 0～100000までの配列
		var _tmp = _random.randi_range(0, 9) # 0～9の整数
		if (_tmp == 0): _i0 += 1
		elif (_tmp == 1): _i1 += 1
		elif (_tmp == 2): _i2 += 1
		elif (_tmp == 3): _i3 += 1
		elif (_tmp == 4): _i4 += 1
		elif (_tmp == 5): _i5 += 1
		elif (_tmp == 6): _i6 += 1
		elif (_tmp == 7): _i7 += 1
		elif (_tmp == 8): _i8 += 1
		elif (_tmp == 9): _i9 += 1
		else: print("Error")
	print([_i0, _i1, _i2, _i3, _i4, _i5, _i6, _i7, _i8, _i9])
	#-> [10045, 10159, 9839, 10011, 10162, 10063, 9772, 9824, 10000, 10125]
```

（注意）**.randomize()** を実行しないと毎回結果が同じになる（＝同じシード値を使用しているため）

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E4%B9%B1%E6%95%B0)]  
参考：[GODOT DOCS](https://docs.godotengine.org/en/latest/classes/class_randomnumbergenerator.html?highlight=RandomNumberGenerator)  
実行環境：Windows 10、Godot Engine 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年02月09日  
更新日：2022年08月14日  
[[TOP](#TOP)]


<a name="202207130907"></a>
# <b>日時情報</b>

### 書式
```gdscript
var XXX = Time.get_datetime_dict_from_system()
XXX.year # 年（2016等）
XXX.month # 月（1〜12）
XXX.day # 日（1〜31）
XXX.weekday() # 0（日曜）〜6（土曜）←Pythonと異なる
XXX.hour # 時間（0〜23）
XXX.minute # 分（0〜59）
XXX.second # 秒（0〜59）
XXX.dst # サマータイム（true or false）
# マイクロ秒を取得する場合 OS.get_system_time_msecs() を利用
```

### 例文
```gdscript
extends Node3D

func _ready():
	var _now = Time.get_datetime_dict_from_system()
	print(_now) #-> {"year":2022, "month":7, "day":13, "weekday":3, "dst":false, "hour":9, "minute":1, "second":17}
	print(_now.year) # 年（2017等）
	print(_now.month) # 月（1〜12）
	print(_now.day) # 日（1〜31）
	print(_now.weekday) #0（日曜）〜6（土曜）←Pythonと異なる
	print(_now.hour) # 時間（0〜23）
	print(_now.minute) # 分（0〜59）
	print(_now.second) # 秒（0〜59）
	
	#"hh:mm:ss"で現在の時間を表示する方法
	var _h = _now.hour
	var _m = _now.minute
	var _s = _now.second
	if _h < 10: _h = "0" + str(_h)
	if _m < 10: _m = "0" + str(_m)
	if _s < 10: _s = "0" + str(_s)
	print(str(_h) + ":" + str(_m) + ":" + str(_s)) #-> "09:04:11"
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E6%97%A5%E6%99%82%E6%83%85%E5%A0%B1)]  
参照：[GODOT DOCS（**Time**）](https://docs.godotengine.org/en/latest/classes/class_time.html?highlight=Time#time)  
実行環境：Windows 10、Godot 4.0 alpha 11  
作成者：夢寐郎  
作成日：2022年01月09日  
更新日：2022年07月13日 Godot 4.0 対応  
[[TOP](#TOP)]


<a name="タイマー"></a>
# <b>タイマー</b>

### 📝 一度だけ実行：推奨
```gdscript
extends Node3D

func _ready():
	print("すぐに実行➀")
	await timeOut()  # ⚠最終行に記述すること

func timeOut():
	print("すぐに実行➁")
	await get_tree().create_timer(3.0).timeout
	print("3.0秒後に一度だけ実行したい処理")
```
参考：[GODOT DOCS](https://docs.godotengine.org/en/latest/classes/class_scenetree.html#class-scenetree-method-create-timer)  

### 📝 一度だけ実行：非推奨  
```gdscript
extends Node3D

func _ready():
	var _timer = Timer.new()
	_timer.set_wait_time(3.0) # 3.0秒後に実行したい場合（初期値1.0）
	_timer.connect("timeout", timeOut)
	_timer.set_one_shot(true)
	self.add_child(_timer) # selfは省略可能
	_timer.start()

func timeOut():
	print("一度だけ実行したい処理")
```

### 📝 繰り返し実行：永久継続  
```gdscript
extends Node3D

func _ready():
	await loop() # ⚠最終行に記述すること

func loop():
	await get_tree().create_timer(1.0).timeout
	print("1.0秒事に実行したい処理")
	await loop()
```

### 📝 繰り返し実行：途中停止
```gdscript
extends Node3D

func _ready():
	var _timer = Timer.new()
	_timer.set_wait_time(1.0) # 1.0秒毎に実行したい場合（初期値1.0）
	_timer.connect("timeout", loop)
	self.add_child(_timer) # selfは省略可能
	_timer.start()
	#_timer.stop() #ループを止める場合

func loop():
	print("繰返し実行したい処理")
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E3%82%BF%E3%82%A4%E3%83%9E%E3%83%BC)]  
実行環境：Windows 10、Godot 4.0 alpha 11  
作成者：夢寐郎  
作成日：2022年02月09日  
作成日：2022年07月13日 Godot 4.0 対応     
[[TOP](#TOP)]


<a name="処理速度計測"></a>
# <b>処理速度計測</b>

```gdscript
# /root/Main(Main.gd)
extends Node3D

func _ready():
	……
	# UNIX時間（1970年1月1日0:00からの経過時間＝秒）
	var _start = Time.get_unix_time_from_system()

	#===========================================
	# ここに計測したい様々な処理を記述
	for i in range(0,100000000): # 1億回繰り返す
		# 速度計測したい処理
		pass # 今回は何もしない
	#===========================================
	
	var _result = Time.get_unix_time_from_system() - _start
	print(str(_result) + " sec.") #-> 1.83999991416931 sec.
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E5%87%A6%E7%90%86%E9%80%9F%E5%BA%A6%E8%A8%88%E6%B8%AC)]  
参考：[GODOT DOCS（**Time**）](https://docs.godotengine.org/en/latest/classes/class_time.html?highlight=datetime#time)  
実行環境：Windows 10、Godot 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年02月09日  
更新日：2022年08月14日  
[[TOP](#TOP)]


<a name="外部テキストの読み込み"></a>
# <b>外部テキストの読み込み</b>

sample.txt
```
あいうえお
かきくけこ
さしすせそ
```

```gdscript
# /root/Main(Main.gd)
extends Node3D
……
func _ready():
	……
	var _file = File.new()
	_file.open("res://sample.txt", File.READ)
	print(_file.get_as_text())
	_file.close()

#-> あいうえお
#-> かきくけこ
#-> さしすせそ
```

[[C# 版](https://github.com/mubirou/HelloWorld/blob/master/languages/C%23Godot/C%23Godot_reference.md#%E5%A4%96%E9%83%A8%E3%83%86%E3%82%AD%E3%82%B9%E3%83%88%E3%81%AE%E8%AA%AD%E3%81%BF%E8%BE%BC%E3%81%BF)]  
参考：[GODOT DOCS（**File**）](https://docs.godotengine.org/en/latest/classes/class_file.html?highlight=File#file)  
実行環境：Windows 10、Godot Engine 4.0 alpha 14  
作成者：夢寐郎  
作成日：2022年02月09日  
更新日：2022年08月14日  
[[TOP](#TOP)]