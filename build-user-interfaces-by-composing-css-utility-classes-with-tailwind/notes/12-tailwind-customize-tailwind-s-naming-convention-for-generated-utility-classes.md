📹[Customize Tailwind’s Naming Convention for Generated Utility Classes](https://egghead.io/lessons/tailwind-customize-tailwind-s-naming-convention-for-generated-utility-classes)

In the event of a conflict between Tailwind's utility classes and those of another library, Tailwind allows custom prefixes and separators to be set in the config file.

```diff
  options: {
-   prefix: "",
+   prefix: "lego"
    important: false,
    separator: ":",
  }
```

> Tip: Remember to recompile Tailwind by running the command `gulp` after editing the config

After Tailwind recompiles, the generated classes will all be prefixed with the word `lego`

* `.lego-bg-blue-500`
* `.lego-text-center`
* `.lego-p-3`

```diff
  options: {
    prefix: "lego"
    important: false,
-   separator: ":",
+   separator: "__",
  }
```

> Tip: Remember to recompile Tailwind by running the command `gulp` after editing the config

The separator affects all of the responsive breakpoints and variants, and appears *before* the custom prefix.

* `.hover__lego-bg-blue-500`
* `.focus__lego-text-center`
* `.md__group-hover__lego-p-3`

Next lesson: [Removing Unused CSS in Tailwind with PurgeCSS](https://egghead.io/lessons/tailwind-removing-unused-css-in-tailwind-with-purgecss)

Previous: [Create a Responsive Card Component by Composing Tailwind's Utility Classes](https://egghead.io/lessons/tailwind-create-a-responsive-card-component-by-composing-tailwind-s-utility-classes)