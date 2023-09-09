<script lang="ts">
  import type { SizeType, StepperColorType } from '$lib/types';
  import { getContext } from 'svelte';
  import { twMerge } from 'tailwind-merge';

  const { size, color }: { size: SizeType; color: StepperColorType } = getContext('stepper');

  export let completed: boolean;
  // export let spanClass: string = 'flex items-center';
  // export let completedClass: string = 'text-blue-600 dark:text-blue-500';
  // export let lastClass: string = 'md:w-auto';
  export let last: boolean;
  export let stepNumber: string = '';
  export let type: 'default' | 'pill' = 'default';

  const liClass = {
    default: 'flex items-center md:w-full',
    pill: 'flex w-full items-center'
  };

  const afterClass = {
    default: "after:content-[''] after:border-1 after:w-full after:h-1 after:border-b after:border-gray-200 after:hidden sm:after:inline-block after:mx-6 dark:after:border-gray-700",
    pill: "after:content-[''] after:w-full after:h-1 after:border-4 after:border-b after:inline-block after:border-gray-100 dark:after:border-gray-700"
  };

  const completedClass = {
    default: 'text-blue-600 dark:text-blue-500',
    pill: 'after:border-blue-100 dark:after:border-blue-800'
  };

  const lastLiClass = {
    default: 'md:w-auto',
    pill: ''
  };

  const spanClass = {
    default: 'flex items-center',
    pill: 'flex items-center justify-center w-10 h-10 rounded-full shrink-0 bg-gray-100 dark:bg-gray-700'
  };

  const completedSpanClass = {
    default: '',
    pill: 'bg-blue-100 dark:bg-blue-800'
  };

  /* $: {
    switch (true) {
      case completed:
        liClass = "flex md:w-full items-center text-blue-600 dark:text-blue-500 sm:after:content-[''] after:w-full after:h-1 after:border-b after:border-gray-200 after:border-1 after:hidden sm:after:inline-block after:mx-6 xl:after:mx-6 dark:after:border-gray-700";
        break;
      case last:
        liClass = 'flex items-center';
        break;
      default:
        liClass = "flex md:w-full items-center";
        break;
    }
  } */
  /* $: {
    switch (true) {
      case round:
        spanClass = 'flex items-center justify-center w-10 h-10 bg-blue-100 rounded-full lg:h-12 lg:w-12 dark:bg-blue-800 shrink-0';
        break;
      default:
        spanClass = "flex items-center after:content-['/'] sm:after:hidden after:mx-2 after:text-gray-200 dark:after:text-gray-500";
        break;
    }
  } */
  $: classLi = twMerge(liClass[type], !last ? afterClass[type] : '', completed ? completedClass[type] : '', last ? lastLiClass[type] : '');
  $: classSpan = twMerge(spanClass[type], completed ? completedSpanClass[type] : '');
</script>

<li class={twMerge(classLi, $$props.class)}>
  <span class={classSpan}>
    {#if completed && $$slots['icon-complete']}
      <slot name="icon-complete" {size} />
    {:else if $$slots.icon}
      <slot name="icon" {size} />
    {/if}
    {#if stepNumber && type === 'default' && !completed}
      <span class="mr-2">{stepNumber}</span>
    {/if}
    <slot />
  </span>
</li>
