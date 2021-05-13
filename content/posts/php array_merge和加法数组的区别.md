```php
<?php
echo "索引数组\n";
$arr1=['e','w','q'];
$arr2=['a','g','h'];
//print_r( $arr1);
//print_r( $arr2);
echo "当是索引数组的时候";
echo "加法";
print_r(  $arr2+$arr1);
echo "merge:";
print_r(array_merge($arr2,$arr1));



echo "关联数组";
$arr3=array('e'=>'f','g'=>'k');
$arr4=array('i'=>'l','g'=>'sa');
//print_r($arr3);
//print_r($arr4);

print_r(array_merge($arr3,$arr4));
echo "后面覆盖前面";
print_r(array_merge($arr4,$arr3));
echo "关联数组加";
print_r($arr3+$arr4);
echo "加法运算，都舍弃相同的键名，后面覆盖前面。只有array_merge才会区别是关联数组（同键名覆盖）还是索引数组(不覆盖)。";
echo "既是索引，又是关联数组呢。";

$arr5=array('i'=>'l','g'=>'sa','gh');
$arr6=array('i'=>'l','g'=>'sa','gh2');
print_r($arr5);
print_r($arr6);
echo "加法：\n";
print_r($arr6+$arr5);
echo "merge\n";
print_r(array_merge($arr6,$arr5));

echo "混合 数组也是一样，分为索引部分和关联部队，merge和加法按各自的方式对待。";
```


```powershell
E:\WorkPlacePHPStorm\PHP74\php.exe E:\WorkPlacePHPStorm\learn\HelloWord\review\1.php
索引数组
当是索引数组的时候加法Array
(
    [0] => a
    [1] => g
    [2] => h
)
merge:Array
(
    [0] => a
    [1] => g
    [2] => h
    [3] => e
    [4] => w
    [5] => q
)
关联数组Array
(
    [e] => f
    [g] => sa
    [i] => l
)
后面覆盖前面Array
(
    [i] => l
    [g] => k
    [e] => f
)
关联数组加Array
(
    [e] => f
    [g] => k
    [i] => l
)
加法运算，都舍弃相同的键名，后面覆盖前面。只有array_merge才会区别是关联数组（同键名覆盖）还是索引数组(不覆盖)。既是索引，又是关联数组呢。Array
(
    [i] => l
    [g] => sa
    [0] => gh
)
Array
(
    [i] => l
    [g] => sa
    [0] => gh2
)
加法：
Array
(
    [i] => l
    [g] => sa
    [0] => gh2
)
merge
Array
(
    [i] => l
    [g] => sa
    [0] => gh2
    [1] => gh
)

Process finished with exit code 0

```


### 总结：
使用array_merge( )，如果是关联数组合并，如果数组的键名相同，那么后面的值将覆盖前者；如果是数字索引数组合并，则不覆盖，而是后者附加到前者后面。使用数组加法运算，与 array_merge( )不同，加法运算不管是关联数组还是数字索引数组，都是将相同键名的值舍弃，也就是只保留首次出现该键名的元素，后来的具有相同键名的元素都不会被加进来。
