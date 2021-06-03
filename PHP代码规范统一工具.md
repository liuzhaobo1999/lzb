# Code风格统一工具


## 代码风格统一的重要性

为什么要强调代码风格统一？很简单：**代码风格统一是项目规范的一部分，统一的良好代码风格可以提高代码的可读性，以至于降低端对沟通维护成本**。



## php-cs-fixer特点

- 可自定义代码风格

- 检查代码风格的同时可自动化修复代码

- 检查代码是否存在编码错误

- 自动优化程序，提高代码的质量与高效性



## 安装与使用

#### 安装

```shell
# 基于composer全局安装
composer global require friendsofphp/php-cs-fixer

# 配置环境变量
export PATH="$PATH:$HOME/.composer/vendor/bin"
```

#### 使用

```shell
# 简洁使用
➜ php-cs-fixer fix /path/src

# 使用实例
➜ php-cs-fixer fix demo.php
@@ @@
 <?php
-function   sum(int $chinese,   int  $math):bool{
-return $chinese+    $math;
-}
+function sum(int $chinese, int $math) : bool
+{
+    return $chinese + $math;
+}
```



## 代码风格配置

可灵活配置是此工具的最优势的一点，团队约定规则配置非常重要，是关键必须的一步，统一代码风格配置好比如一个团队的榜样旗。如下为推荐的使用配置

```php
<?php
$header = <<<EOF
What php team is that is 'one thing, a team, work together'
EOF;

$finder = PhpCsFixer\Finder::create()
    ->files()
    ->name('*.php')
    ->exclude('vendor')
    ->in(__DIR__)
    ->ignoreDotFiles(true)
    ->ignoreVCS(true);

$rules  = array(
    '@Symfony'                                   => true,
    'header_comment'                             => array('header' => $header),
    'array_syntax'                               => array('syntax' => 'short'),
    'ordered_imports'                            => true, // 按顺序use导入
    'no_useless_else'                            => true, // 删除没有使用的else节点
    'no_useless_return'                          => true, // 删除没有使用的return语句
    'self_accessor'                              => true, // 在当前类中使用 self 代替类名
    'php_unit_construct'                         => true,
    'single_quote'                               => true, // 简单字符串应该使用单引号代替双引号
    'no_unused_imports'                          => true, // 删除没用到的use
    'no_singleline_whitespace_before_semicolons' => true, // 禁止只有单行空格和分号的写法
    'no_empty_statement'                         => true, // 多余的分号
    'no_whitespace_in_blank_line'                => true, // 删除空行中的空格
    'standardize_not_equals'                     => true, // 使用 <> 代替 !=
    'combine_consecutive_unsets'                 => true, // 当多个 unset 使用的时候，合并处理
    'concat_space'                               => ['spacing' => 'one'], // .拼接必须有空格分割
    'array_indentation'                          => true, // 数组的每个元素必须缩进一次
    'blank_line_before_statement'                => [
        'statements' => [
            'break',
            'continue',
            'declare',
            'return',
            'throw',
            'try'
        ]
    ],// 空行换行必须在任何已配置的语句之前
    'binary_operator_spaces'                     => [
        'default' => 'align_single_space'
    ], //等号对齐、数字箭头符号对齐
    'align_multiline_comment'                    => [
        'comment_type' => 'phpdocs_only'
    ],
    'lowercase_cast'                             => true,// 类型强制小写
    'lowercase_constants'                        => true,// 常量为小写
    'lowercase_static_reference'                 => true,// 静态调用为小写
    'no_blank_lines_after_class_opening'         => true,
    'phpdoc_separation'                          => false,// 不同注释部分按照单空行隔开
    'phpdoc_single_line_var_spacing'             => true,
    'phpdoc_indent'                              => true,
    'no_superfluous_phpdoc_tags'                 => false,// 删除没有提供有效信息的@param和@return注解
    'phpdoc_align'                               => [
        'align' => 'vertical',
        'tags'  => [
            'param', 'throws', 'type', 'var', 'property'
        ]
    ]
);

return PhpCsFixer\Config::create()
    ->setRiskyAllowed(true)
    ->setRules($rules)
    ->setFinder($finder);

```

项目的代码风格统一配置文件放置于项目的根目录，默认的命名为`.php_cs`。

一般而言，我们使用此工具来统一我们编写的 `PHP` 源码文件，在`Laravel`中，一般修复`app` 与 `config` 目录下的所有文件。

```shell
# 统一修复
php-cs-fixer app && php-cs-fixer config
```

常规的做法我们将我们改动过的文件即可，我的常规操作~

```shell
# 针对某次改动的文件进行修复，对证下药
git status -s app | xargs php-cs-fixer 
```



































