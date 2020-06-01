# svelte-procedures

There are times when a set of actions must be done in "procedures". For
instance, you might need a step-by-step form that requires a fetch call to
validate user's input. `svelte-procedures` is a package that assists you through such design patterns.

## Installation

```
npm i -D svelte-proceduers
```

## How to

Import `Procedures` from the package, and import your own "procedure" components.

Map them in an array with the following structure, then place the array as a property within the Procedures component.

See under `example` for detailed instructions.

```html
<script>
    import Procedures from "svelte-procedures";

    import Introduction from "./procedures/introduction.svelte";
    import Introduction2 from "./procedures/introduction-2.svelte";
    import ViewText from "./procedures/view-text.svelte";

    const procedures = [
        {
            name: "Introduction",
            component: Introduction,
        },
        {
            name: "Introduction 2",
            component: Introduction2,
        },
        {
            name: "View Text Data",
            component: ViewText,
        },
    ];
</script>

<div class="root">
    <div class="centerbox">
        <h1>Svelte Procedures</h1>
        <Procedures {procedures} />
    </div>
</div>
```

## Customizing Progress Indicator

The default progress indicator is implemented in `Progress.svelte`.

You could use your own implementation of progress indicator using named slots.

`procedures` and `currentStepIndex` will be passed as props to the named slot `progress`.

## License

MIT
