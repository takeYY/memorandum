# Rubyに関するまとめ
## メソッド
括弧()を省略可能
- map
    - 渡されたブロック{}を配列や範囲オブジェクトの各要素に対して適用
    ```ruby=
    オブジェクト.map {|変数|
      #実行する処理1
      #実行する処理2
    }
    ```
- upcase
    - 文字列に対して、大文字にして返す
- downcase
    - 文字列に対して、小文字にして返す
- times
    - 変数に「0」から「（対象のオブジェクトが持つ数値） - 1」を順に代入しながら、ブロック{}内の処理(又は「do」から「end」までの処理)を実行
    - 繰り返す毎に+1、|変数|の部分は省略可能
    ```ruby=
    # 例１
    オブジェクト.times{|変数|
      #実行する処理1
      #実行する処理2
    }
    
    # 例２
    オブジェクト.times do |変数|
      #実行する処理1
      #実行する処理2
    end
    ```
- upto
    - 変数に「対象のオブジェクトが持つ数値」から「max」を順に代入しながら、ブロック{}内の処理(又は「do」から「end」までの処理)を実行
    - 繰り返す毎に+1、|変数|の部分は省略可能
    ```ruby=
    # 例１
    オブジェクト.upto(max){|変数|
      #実行する処理1
      #実行する処理2
    }
    
    # 例２
    オブジェクト.upto(max) do |変数|
      #実行する処理1
      #実行する処理2
    end
    ```
- downto
    - 変数に「対象のオブジェクトが持つ数値」から「min」を順に代入しながら、ブロック内の処理(又は「do」から「end」までの処理)を実行
    - 繰り返す毎に-1、|変数|の部分は省略可能
    ```ruby=
    # 例１
    オブジェクト.downto(min){|変数|
      #実行する処理1
      #実行する処理2
    }
    
    # 例２
    オブジェクト.downto(min) do |変数|
      #実行する処理1
      #実行する処理2
    end
    ```
- each
    - 配列や範囲オブジェクトなどで用意されているメソッド
    - オブジェクトに含まれている要素を順に取り出す
    - for文とほとんど同じ動きをする
    ```ruby=
    # 例１
    オブジェクト.each{|変数|
      #実行する処理1
      #実行する処理2
    }
    
    # 例２
    オブジェクト.each do |変数|
      #実行する処理1
      #実行する処理2
    end
    
    # 例３
    for 変数 in オブジェクト do
      #実行する処理1
      #実行する処理2
    end
    ```
- inspectメソッド
    - 要求されたオブジェクトを表現する文字列を返す
    ```ruby=
    puts (1..5).to_a            # 配列を文字列として出力
    # 1
    # 2
    # 3
    # 4
    # 5
    
    puts (1..5).to_a.inspect    # 配列のリテラルを出力
    # [1, 2, 3, 4, 5]
    
    puts :name, :name.inspect
    # name
    # :name
    
    puts "It worked!", "It worked!".inspect
    # It worked!
    # "It worked!"
    ```
- pメソッド
    - inspectメソッドのショートカット
    ```ruby=
    p :name        # 'puts :name.inspect'　と同じ
    # :name
    ```
## 文字列
- 空かどうか
```ruby=
puts "".empty?
# true

puts "foo".empty?
# false
```

- 長さ
```ruby=
puts "test".length
# 4
```

- 変数展開
```ruby=
pref = "東京都"
city = "足立区"
puts "#{pref}_#{city}"
# 東京都_足立区
```

- 文字列に変換
```ruby=
num = 1
puts num.to_s
# 1

puts nil.to_s
#
```

## 条件
- 論理値
```ruby=
### and ###
puts "trueDAO" if "" == nil.to_s && "1" == "1".to_s
# trueDAO

### or ###
puts "trueDAO2" if 0<1 || 0 >= 1
# trueDAO2

### not ###
puts "trueDAO3" if !false
# trueDAO3
```

- unless（偽の時に実行）
```ruby=
s = "test"
puts "「#{s}」 is not empty." unless s.empty?
# 「test」 is not empty.
```

- !!(bang bang)
```ruby=
puts !!nil
# false

puts !!0
# true

##########
puts !0
# false
##########
```

## 空のオブジェクト判定
```ruby=
puts nil.nil?
# true
```

## メソッド
- メソッドの引数の省略
```ruby=
def test_func(str = "setup")
    puts str
end

test_func("test")
# test
test_func
# setup
test_func("")
# setup
```

## 配列と範囲演算子
- 配列に要素を追加
```ruby=
test = []
test.push(3)
# [3]

test << 5
# [3, 5]

test << "foo" << 8
# [3, 5, "foo", 8]
```

- 文字列を配列に分割
```ruby=
ar = "foo bar     baz".split
ar
# ["foo", "bar", "baz"]
```

- インデックス
```ruby=
puts ar[1]
# "bar"

puts ar[-3]
# "foo"

puts ar.first
# "foo"

puts ar.second
# "bar"
```

- 配列に要素が含まれるか
```ruby=
puts ar.include?("baz")
# true
```

- 範囲
```ruby=
0..9
# 0..9

(0..9).to_a
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

- 文字列の配列に変換
```ruby=
a = %w[foo bar baz quux]
# ["foo", "bar", "baz", "quux"]

a[0..2]
# ["foo", "bar", "baz"]

a[0..-1]
# ["foo", "bar", "baz", "quux"]
```

## ブロック
- 1行
```ruby=
(1..5).each{ |i| puts 2*i }
# 2
# 4
# 6
# 8
# 10
```

- 複数行
```ruby=
(1..5).each do |number|
    puts 2*number
    puts "--"
end
# 2
# --
# 4
# --
# 6
# --
# 8
# --
# 10
# --
```

- ブロックに変数を用いない例
```ruby=
3.times{puts "Glory!"}
# "Glory!"
# "Glory!"
# "Glory!"
```

- mapメソッドを用いる例
```ruby=
(1..5).map{ |i| i**2 }    # i^2
# [1, 4, 9, 16, 25]

abc = %w[a b c]
# ["a", "b", "c"]

abc.map{ |char| char.upcase }
# ["A", "B", "C"]

abc.map{ &:upcase }
# ["A", "B", "C"]
```

## ハッシュ（辞書）
```ruby=
# 初期化
numbers = {}

# キーとバリューの追加
numbers["first"] = "1st"
numbers["second"] = "2nd"

# 表示
puts numbers
# {"first"=>"1st", "second"=>"2nd"}

# これでも良い
nums = {"first"=>"1st", "second"=>"2nd", "third"=>"3rd"}
puts nums
# {"first"=>"1st", "second"=>"2nd", "third"=>"3rd"}
```

## シンボル
文字列として扱うことができるが、それよりも高速で処理が可能
値の変更は不可能
```ruby=
puts "name".split("")
# ["n", "a", "m", "e"]

:name.split("")
# NoMethodError: undifined method 'split' for :name:Symbol


user1 = {:name=>"turing", :email=>"turing@example.com"}
# {:name=>"turing", :email=>"turing@example.com"}
puts user1[:name]
# "turing"
puts user1[:email]
# turing@example.com

user2 = {name: "turing", email: "turing@example.com"}
# {:name=>"turing", :email=>"turing@example.com"}
user1 == user2
# true
```
- ハッシュのハッシュ
```ruby=
params = {}
params[:user] = {name:"turing", email:"apple@example.com"}
puts params
# {:user=>{:name=>"turing", :email=>"apple@example.com"}}
puts params[:user][:email]
# "apple@example.com"
```

- ハッシュでeachメソッド
```ruby=
flash = {success:"It worked!", danger:"It failed..."}
flash.each do |key, value|
    puts "Key #{key.inspect} has value #{value.inspect}"
end
# Key :success has value "It worked!"
# Key :danger has value "It failed..."
```

###### tags: `program`,`プログラム`
