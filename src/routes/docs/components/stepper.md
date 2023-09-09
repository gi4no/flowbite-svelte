---
layout: componentLayout
title: Svelte Stepper - Flowbite
breadcrumb_title: Svelte Stepper
component_title: Stepper
dir: Components
description: Use the stepper component to show the number of steps required to complete a form inside your application based on Tailwind CSS
thumnailSize: w-48
---

<script>
  import { TableProp, TableDefaultRow, CompoAttributesViewer } from '../../utils'
  import { P, A } from '$lib'
  import componentData1 from '../../component-data/Stepper.json'
  const components = 'Stepper'
</script>

The stepper component can be used to show a numbered list of steps next to a form component to indicate the progress and number of steps that are required to complete and submit the form data.

There are multiple examples that you can use including horizontal or vertical aligned stepper components, different sizes, styles, and showing icons or numbers all coded with the utility classes from Tailwind CSS.

## Setup

Import the `Stepper` component in a script tag.

```svelte example hideOutput
<script>
  import { Stepper } from 'flowbite-svelte';
</script>
```

## Default stepper

Use this example to show a list of form steps with a number and title of the step in a horizontal alignment.

```svelte example
<script>
  import { Stepper, StepperStep } from 'flowbite-svelte';
  import { CheckCircleSolid } from 'flowbite-svelte-icons';
</script>

<Stepper>
  <StepperStep stepNumber="1" completed>
    <CheckCircleSolid slot="icon-complete" class="mr-2.5" />
    Personal <span class="hidden sm:inline-flex sm:ml-2">Info</span>
  </StepperStep>
  <StepperStep stepNumber="2">
    <CheckCircleSolid slot="icon-complete" class="mr-2.5" />
    Account <span class="hidden sm:inline-flex sm:ml-2">Info</span>
  </StepperStep>
  <StepperStep stepNumber="3" last>
    <CheckCircleSolid slot="icon-complete" class="mr-2.5" />
    Confirmation
  </StepperStep>
</Stepper>
```

## Progress stepper

This example can be used to show the progress of the stepper component based only on icons and showing a checkmark when the step has been finished.

```svelte example
<script>
  import { Stepper, StepperStep } from 'flowbite-svelte';
  import { CheckSolid, ProfileCardOutline, ClipboardCheckSolid } from 'flowbite-svelte-icons';
</script>

<Stepper size="sm">
  <StepperStep stepNumber="1" completed type="pill">
    <CheckSolid slot="icon-complete" let:size size={size} />
  </StepperStep>
  <StepperStep stepNumber="2" type="pill">
    <ProfileCardOutline slot="icon" completed let:size size={size} />
    <CheckSolid slot="icon-complete" let:size size={size} />
  </StepperStep>
  <StepperStep stepNumber="3" last type="pill">
    <ClipboardCheckSolid slot="icon" let:size {size} />
  </StepperStep>
</Stepper>
```

## Detailed stepper

Use this example to show an extra subtitle next to the number and the title of the steppper component based on an ordered list element.

```svelte example
<script>
  import { Stepper, StepperStep } from 'flowbite-svelte';
  import { CheckSolid, ProfileCardOutline, ClipboardCheckSolid } from 'flowbite-svelte-icons';
</script>

<Stepper size="sm">
  <StepperStep stepNumber="1" completed type="detailed">
    <CheckSolid slot="icon-complete" let:size size={size} />
  </StepperStep>
  <StepperStep stepNumber="2" type="detailed">
    <ProfileCardOutline slot="icon" completed let:size size={size} />
    <CheckSolid slot="icon-complete" let:size size={size} />
  </StepperStep>
  <StepperStep stepNumber="3" last type="detailed">
    <ClipboardCheckSolid slot="icon" let:size {size} />
  </StepperStep>
</Stepper>
```

## Component data

The component has the following props, type, and default values. See [types page](/docs/pages/typescript) for type information.

### Progressbar styling

- Use the `class` prop to overwrite the `div` class.
- Use the `classLabelOutside` prop to overwrite the outside `div` class.

<CompoAttributesViewer {components}/>

## References

- [Flowbite Progress Bar](https://flowbite.com/docs/components/progress/)
