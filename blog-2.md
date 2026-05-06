# Pick & Omit in TypeScript: Keep Your Code DRY

## 📌 Introduction

When building applications, we often work with large interfaces. But not every part of that interface is needed everywhere. Writing new types again and again leads to duplication and messy code.

TypeScript solves this problem with two powerful utility types: **Pick** and **Omit**.

---

## The Problem (Code Duplication)

Consider this interface:

```ts
interface User {
  id: number;
  name: string;
  email: string;
  password: string;
}
```

Now imagine:

* For public profile → you don’t need `password`
* For login → you only need `email` and `password`

Creating new interfaces manually would repeat code 

---

## Using `Pick`

`Pick` allows you to select only specific properties.

```ts
type PublicUser = Pick<User, "id" | "name">;

const user: PublicUser = {
  id: 1,
  name: "Mahfuz"
};
```

 Only selected fields are included

---

## Using `Omit`

`Omit` removes specific properties from a type.

```ts
type SafeUser = Omit<User, "password">;

const user: SafeUser = {
  id: 1,
  name: "Mahfuz",
  email: "mahfuz@example.com"
};
```

 Everything except `password`

---

## Why This Matters (DRY Principle)

DRY = **Don't Repeat Yourself**

Without Pick/Omit:

* Duplicate code 
* Hard to maintain 

With Pick/Omit:

* Reuse existing types ✅
* Cleaner and shorter code ✅
* Easier to maintain ✅

---

## Real-Life Analogy

Think of a big pizza 

* `Pick` → you take only slices you want
* `Omit` → you remove slices you don’t want

---

## Conclusion

* `Pick` = choose what you need
* `Omit` = remove what you don’t need
* Keeps your code DRY, clean, and maintainable

 These small tools can make a big difference in writing professional TypeScript code 
