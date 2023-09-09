<script lang="ts">
  import type { SizeType, StepperColorType } from '$lib/types';
  import { setContext } from 'svelte';
  import { twMerge } from 'tailwind-merge';

  export let olClass = 'flex items-center w-full font-medium';
  export let size: SizeType = 'md';
  export let color: StepperColorType = 'primary';

  const colorClasses = {
    alternative: 'text-gray-900 dark:text-gray-400',
    blue: 'text-blue-900 dark:text-gray-400',
    dark: 'text-gray-900 dark:text-gray-400',
    green: 'text-green-900 dark:text-gray-400',
    light: 'text-white-900 dark:text-gray-400',
    primary: 'text-gray-500 dark:text-gray-400',
    purple: 'text-purple-900 dark:text-gray-400',
    red: 'text-red-900 dark:text-gray-400',
    yellow: 'text-yellow-900 dark:text-gray-400',
    none: ''
  };

  const sizeClasses = {
    xs: 'text-xs',
    sm: 'text-sm',
    md: 'text-md',
    lg: 'text-lg',
    xl: 'text-xl'
  };

  setContext('stepper', { size, color });

  $: olWrapperClass = twMerge(olClass, sizeClasses[size], colorClasses[color]);
</script>

<ol class={twMerge(olWrapperClass, $$props.class)}>
  <slot {color} />
</ol>
