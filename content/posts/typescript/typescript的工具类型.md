---
title: "Typescript的工具类型"
date: 2021-05-06T11:55:33+08:00
summary: "replace with summary"
showToc: true
ShowBreadCrumbs: true
draft: true
cover:
  image: "default.jpg"
  alt: "default"
  caption: "<text>"
  relative: false
  hidden: false
---

## Partial< Type >

> 构造一个类型，将传入 `Type` 的所有属性设置为可选。将返回一个表示给定类型的所有子集的类型

这里是[源码](https://github.com/microsoft/TypeScript/blob/8da3eff7b0dbb68c17a950c006edf143456b28cc/src/lib/es5.d.ts#L1421)对其的定义：

```ts
/**
 * Make all properties in T optional
 */
type Partial<T> = {
  [P in keyof T]?: T[P];
};
```

举个 🌰

```ts
type Person = {
  name: string;
  age: number;
};

type Something = Partial<Person>;
// 等价于
type Something = {
  name?: string;
  age?: number;
};
```

## Required< Type >

> 构造一个类型，该类型将为传入的 `Type` 所有 `key` 设置为 required 的所有属性。与 `Partial` 相反。

同样是一个非常常用的高级类型,这里是[源码](https://github.com/microsoft/TypeScript/blob/8da3eff7b0dbb68c17a950c006edf143456b28cc/src/lib/es5.d.ts#L1428)对其的定义：

```ts
/**
 * Make all properties in T required
 */
type Required<T> = {
  [P in keyof T]-?: T[P];
};
```

其中涉及到的`-?`是`typescript 2.8`为映射类型添加的补丁，即操作装饰符

举个应用 🌰

```ts
type Person = {
  name: string;
  age?: number;
};

type Something = Required<Person>;
// 等价于
type Something = {
  name: string;
  age: number;
};
```

## Readonly< Type >

> 构造一个 Type 的所有属性都设置为 readonly 的类型，意味着无法重新分配所构造类型的属性。

这里是[源码](https://github.com/microsoft/TypeScript/blob/8da3eff7b0dbb68c17a950c006edf143456b28cc/src/lib/es5.d.ts#L1435)对其的定义：

```ts
/**
 * Make all properties in T readonly
 */
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};
```

举个应用 🌰

```ts
type Person = {
  name: string;
  age?: number;
};

type Something = Readonly<Person>;
// 等价于
type Something = {
  readonly name: string;
  readonly age?: number;
};

const a: Something = {
  name: "zhangsan",
  age: 31,
};

a.age = 30; // Cannot assign to 'age' because it is a read-only property.
```

## Record<Keys,Type>

> 构造一个 Type 的属性为 Keys，类型为 Type 的对象类型。通常将一个类型的属性映射到另一个类型上

这里是[源码](https://github.com/microsoft/TypeScript/blob/8da3eff7b0dbb68c17a950c006edf143456b28cc/src/lib/es5.d.ts#L1449)对其的定义：

```ts
/**
 * Construct a type with a set of properties K of type T
 */
type Record<K extends keyof any, T> = {
  [P in K]: T;
};
```

举个应用 🌰

```ts
type Fruits = {
  apple: string;
  banana: string;
};

type Attributes = {
  from: string;
  color: string;
};

type Something = Record<Fruits, Attributes>;
// 等价于
type Something = {
  apple: Attributes;
  banana: Attributes;
};

const a: Something = {
  apple: {
    from: "south",
    color: "red",
  },
  age: {
    from: "north",
    color: "yellow",
  },
};
```

## Pick<Type,Keys>

> 通过对 Type 的属性进行挑选组成新的类型

这里是[源码](https://github.com/microsoft/TypeScript/blob/8da3eff7b0dbb68c17a950c006edf143456b28cc/src/lib/es5.d.ts#L1442)对其的定义：

```ts
/**
 * From T, pick a set of properties whose keys are in the union K
 */
type Pick<T, K extends keyof T> = {
  [P in K]: T[P];
};
```

举个应用 🌰

```ts
type Person = {
  name: string;
  age: number;
};

type Something = Pick<Person, "age">;
// 等价于
type Something = {
  age: number;
};

const a: Something = {
  age: 11,
};
```

## Omit<Type, Keys>

> 通过对 Type 的属性进行舍弃组成新的类型，与 Pick 相反

这里是[源码](https://github.com/microsoft/TypeScript/blob/8da3eff7b0dbb68c17a950c006edf143456b28cc/src/lib/es5.d.ts#L1466)对其的定义：

```ts
/**
 * Construct a type with the properties of T except for those in type K.
 */
type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>;
```

举个应用 🌰

```ts
type Person = {
  name: string;
  age: number;
};

type Something = Pick<Person, "age">;
// 等价于
type Something = {
  age: number;
};

const a: Something = {
  age: 11,
};
```
