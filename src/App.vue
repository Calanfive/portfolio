<script setup lang="ts">
defineProps<{ msg: string }>();

import Button from './components/ui/button/Button.vue';
import {
    Carousel,
    CarouselContent,
    CarouselItem,
    CarouselNext,
    CarouselPrevious,
} from '@/components/ui/carousel';
import Card from './components/ui/card/Card.vue';
import {
    Tooltip,
    TooltipContent,
    TooltipProvider,
    TooltipTrigger,
} from '@/components/ui/tooltip';
</script>

<template>
    <div class="w-full h-screen bg-stone-900 flex justify-evenly items-center">
        <div class="flex-col w-1/2 items-center">
            <h1 class=" uppercase font-semibold text-2xl text-white p-1 bg-stone-900">Camille LE LAN - Developpeur</h1>
            <div
                class="border-solid border border-white rounded-lg"
            >
                <p class="text-white m-2">
                    Lorem Ipsum is simply dummy text of the printing and
                    typesetting industry. Lorem Ipsum has been the industry's
                    standard dummy text ever since the 1500s, when an unknown
                    printer took a galley of type and scrambled it to make a
                    type specimen book. It has survived not only five centuries,
                    but also the leap into electronic typesetting, remaining
                    essentially unchanged.
                </p>
            </div>
        </div>
        <div class="flex-col w-1/4 items-center justify-end p-4">
            <Carousel
                v-slot="{ canScrollNext }"
                class="relative w-full max-w-xs"
            >
                <CarouselContent>
                    <CarouselItem v-for="(_, index) in 5" :key="index">
                        <div class="p-1">
                            <Card>
                                <CardContent
                                    class="flex aspect-square items-center justify-center p-6"
                                >
                                    <span
                                        class="text-white text-4xl font-semibold"
                                        >{{ index + 1 }}</span
                                    >
                                </CardContent>
                            </Card>
                        </div>
                    </CarouselItem>
                </CarouselContent>
                <CarouselPrevious />
                <CarouselNext v-if="canScrollNext" />
            </Carousel>
            <TooltipProvider>
                <Tooltip>
                    <TooltipTrigger as-child>
                        <Button variant="outline"> Select project </Button>
                    </TooltipTrigger>
                    <TooltipContent>
                        <p>Click for more details</p>
                    </TooltipContent>
                </Tooltip>
            </TooltipProvider>
        </div>
    </div>
</template>
