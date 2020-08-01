# The "x" Naming Convention

Save time and brain cycles when naming (and finding) things in your codebase!

* This document describes a naming convention for lazy developers
* It is a mechanical convention: It is easy to figure out where things go, and where to find them when needed
* The main explanation is for JS/Python/Ruby-like languages, but the same concepts apply to other languages (including Java). More on that at the end.

Summary:
```
/src/x/{topic}/code.js
/src/x/{topic1}__{topic2}/code.js
```

# Step 1: /src/x

* Create an "x" folder or package at the root level (for example 'src/x')

```
src/x/ <--- this is a folder
```

# Step 2: /src/x/{topic}

* Inside this folder, you'll create "topic" folders
* These folders act like index entries and help you organize your code
* Instead of creating these names out of thin air, you will reuse (or "shadow") existing namespaces (for example, NPM)

```
src/x/lodash/ <--- all code that's closely related to the "lodash" package goes here
src/x/stripe/ <--- all code that's closely related to the "stripe" npm package goes here
```

# Step 3: /src/x/{topic}/code.js

* Within these folders, you add the actual code
* Keep the files small. Ideally each file contains only one function/class
* Be as granular as possible

```
src/x/stripe/setupStripeClientUtil.js
src/x/stripe/getStripeTokens.js
```

* If you want, you can shorten the filenames since they're a bit redundant (Date/compareDate --> Date/compare.js)
* if you don't mind snake_case, you can even use more descriptive names that are still deterministic and might help with auto-complete (Date/Date_compare.js)

# Step 4: /src/x/{topic1}__{topic2}

* Sometimes you'll write code that isn't clearly related to "one" particular NPM package, but to 2 or more.
* In this case, you can create an x folder with two names separated by a double underscore

```
src/x/graphql__react/MyGraphQLProviderHOC.js
```

* The topic names are sorted alphabetically (so it will always be "graphql__react" and not "react__graphql")
* Keep things mechanical and deterministic!

# That's it! here are some tips...

* You'll notice that most things will fall naturally into one of these "x/{name}" folders
* You can even create folders for top-level concepts like Array, Date, etc

```
src/x/Date/compareDates.js
src/x/Array/arrayStartsWith.js
```

* Avoid having generic "util" folders
* Not all your code will fit in the x folder
* Some of your code is actually part of your own domain model, or problem. That's fine, you'll put it anywhere you want
* The "x" folder is for code that is granular, simple, utilitarian, and clearly related to external packages. In other words, it is what you would normally store in a "util", "helper" or "etc" folder.
