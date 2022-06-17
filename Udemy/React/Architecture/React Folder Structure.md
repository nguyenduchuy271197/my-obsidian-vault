```
- src/
--- feature/
----- user/
------- profile/
------- avatar/
----- message/
------- message-item/
------- message-list/
----- payment/
------- payment-form/
------- payment-wizard/
----- error/
------- error-message/
------- error-boundary/
--- components/
----- app/
----- list/
----- input/
----- button/
----- checkbox/
----- radio/
----- dropdown/
```

Like in the example above, in a perfect world, we would be using a [kebab-case naming convention](https://www.robinwieruch.de/javascript-naming-conventions/) for all folders and files, because PascalCase named folders/files are handled differently in the diversity of operating systems which may lead to bugs when working with teams using different OSs.

## BONUS: NEXT.JS PROJECT STRUCTURE

A Next.js project starts with a _pages/_ folder. A common question here: Where to put the _src/_ folder?

```
- api/
- pages/
- src/
--- feature/
--- components/
```

Usually the source folder gets created next to the pages folder. From there, you can follow the previously discussed folder/file structure within the _src/_ folder. I heard about an escape hatch in Next.js where you can put the _pages/_ folder in the _src/_ folder too:

```
- api/
- src/
--- pages/
--- feature/
--- components/
```

However, in this case it's not allowed to have a _pages/_ folder anymore.

Reference: https://www.robinwieruch.de/react-folder-structure/

Check it out!
- [ ] https://profy.dev/article/react-folder-structure