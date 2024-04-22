# 						TypeScript学习记录

## 15 tsconfig.json文件内容解析

- “include”:[]
  - 编译指定文件
- “exclude”:[]
  - 与include相反
- “target”:[]
  - 指定编译js 的版本例如es5 es6
- “allowJs”: false
  - 是否允许编译js文件
- “outDir”: “./dist”
  - 指定编译后的存放目录
- “rootDir”: “”
  - 编译文件的目录
- “module“: “ES6”
  - 默认common.js 可选es6模式 amd umd 等
- “removeComments”: “”
  - 是否在编译过程中删除文件中的注释
- “sourceMap”: “”
  - 代码源文件
- “strict”: false
  - 严格模式

## 16 namespace命名空间

我们在工作中无法避免[全局变量](https://so.csdn.net/so/search?q=全局变量&spm=1001.2101.3001.7020)造成的污染，TypeScript提供了namespace 避免这个问题出现

- 内部模块，主要用于组织代码，避免命名冲突。
- 命名空间内的类默认私有
- 通过 `export` 暴露
- 通过 `namespace` 关键字定义

[TypeScript](https://so.csdn.net/so/search?q=TypeScript&spm=1001.2101.3001.7020)与ECMAScript 2015一样，任何包含顶级`import`或者`export`的文件都被当成一个模块。相反地，如果一个文件不带有顶级的`import`或者`export`声明，那么它的内容被视为全局可见的（因此对模块也是可见的）

## 17 三斜线指令

三斜线指令是包含单个XML标签的单行注释。 注释的内容会做为编译器指令使用。

三斜线指令仅可放在包含它的文件的最顶端。 一个三斜线指令的前面只能出现单行或多行注释，这包括其它的三斜线指令。 如果它们出现在一个语句或声明之后，那么它们会被当做普通的单行注释，并且不具有特殊的涵义。

/// <reference path="..." />指令是三斜线指令中最常见的一种。 它用于声明文件间的依赖。

/// <reference type="..." />引入声明文件

三斜线引用告诉编译器在编译过程中要引入的额外的文件。

你也可以把它理解能import，它可以告诉编译器在编译过程中要引入的额外的文件

## 18 声明文件d.ts

当使用[第三方库](https://so.csdn.net/so/search?q=第三方库&spm=1001.2101.3001.7020)时，我们需要引用它的声明文件，才能获得对应的代码补全、接口提示等功能。

```tsx
declare var 声明全局变量
declare function 声明全局方法
declare class 声明全局类
declare enum 声明全局枚举类型
declare namespace 声明（含有子属性的）全局对象
interface 和 type 声明全局类型
/// <reference  三斜线指令
```

