<script setup lang="ts">
import type { HTMLAttributes } from 'vue';
import { cn } from '@/lib/utils';

const props = defineProps<{
    class?: HTMLAttributes['class'];
}>();
</script>

<template>
    <div
        :class="
            cn(
                'rounded-lg border bg-stone-900 text-card-foreground shadow-sm',
                props.class,
            )
        "
    >
        <slot />
    </div>
</template>
