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
import { Skeleton } from '@/components/ui/skeleton';
import Input from './components/ui/input/Input.vue';
import Label from './components/ui/label/Label.vue';
import {
  Sheet,
  SheetClose,
  SheetContent,
  SheetDescription,
  SheetFooter,
  SheetHeader,
  SheetTitle,
  SheetTrigger,
} from '@/components/ui/sheet'
import { ref } from 'vue';
const username = ref('')
const SHEET_SIDES = ['right'] as const
</script>

<template>
    <div class="w-full h-screen bg-gradient-to-b from-black via-yellow-700 to-black flex justify-evenly items-center">

        <div class="flex-col w-1/2 items-center">
            <h1 class=" uppercase font-semibold text-2xl text-white text-opacity-90 p-1">Camille LE LAN - Developpeur</h1>
            <div
                class="border-solid border border-white rounded-lg">
                <p class="text-white text-opacity-80 m-2">
                    Lorem Ipsum is simply dummy text of the printing and
                    typesetting industry. Lorem Ipsum has been the industry'sz
                    standard dummy text ever since the 1500s, when an unknown
                    printer took a galley of type and scrambled it to make a
                    type specimen book. It has survived not only five centuries,
                    but also the leap into electronic typesetting, remaining
                    essentially unchanged.
                </p>
            </div>
            <div class="grid grid-cols-2 gap-2">
                <Sheet v-for="side in SHEET_SIDES" :key="side">
                    <SheetTrigger as-child>
                        <Button variant="outline">
                        {{ side }}
                        </Button>
                    </SheetTrigger>
                    <SheetContent :side="side">
                        <SheetHeader>
                            <SheetTitle>Demande de contact</SheetTitle>
                            <SheetDescription>
                                Merci de l'intérêt que vous portez à mon travail. 
                                Je vous répondrai dans les plus brefs délais.
                            </SheetDescription>
                        </SheetHeader>
                        <div class="grid gap-4 py-4">
                            <div class="grid items-center grid-cols-4 gap-4">
                                <Label for="name" class="text-right">Nom</Label>
                                <Input id="name" v-model="username" class="col-span-3" />
                            </div>
                            <div class="grid items-center grid-cols-4 gap-4">
                                <Label for="username" class="text-right">Prénom</Label>
                                <Input id="username" v-model="username" class="col-span-3" />
                            </div>
                            <div class="grid items-center grid-cols-4 gap-4">
                                <Label for="company" class="text-right">Société</Label>
                                <Input id="company" v-model="username" class="col-span-3" />
                            </div>
                        </div>
                        <SheetFooter>
                            <SheetClose as-child>
                                <Button type="submit">
                                    Envoyer le message
                                </Button>
                            </SheetClose>
                        </SheetFooter>
                    </SheetContent>
                </Sheet>
            </div>
        </div>
        <div class="flex-col justify-items-center-w-1/4 p-2">
            <Carousel
                v-slot="{ canScrollNext }"
                class="relative w-full max-w-xs">
                <CarouselContent>
                    <CarouselItem v-for="(_, index) in 5" :key="index">
                        <div class="p-1">
                            <Card>
                                <CardContent
                                    class="flex flex-col aspect-square items-center justify-center p-6">
                                    <div class="flex flex-col space-y-2">
                                        <span
                                            class="text-white text-4xl font-semibold animate-pulse "
                                            >{{ index + 1 }}
                                        </span>
                                        <div class="space-y-2">
                                            <Skeleton class="h-28 w-[200px]" />
                                            <p class="text-white animate-pulse">coming soon
                                            </p>
                                        </div>
                                    </div>
                                </CardContent>
                            </Card>
                        </div>
                    </CarouselItem>
                </CarouselContent>
                <CarouselPrevious />
                <CarouselNext v-if="canScrollNext" />
            </Carousel>
            <div class="flex justify-end p-1 pr-2">
                <TooltipProvider>
                    <Tooltip>
                        <TooltipTrigger as-child>
                            <Button class="hover:bg-blue-800 hover:text-white"   variant="outline"> Select project </Button>
                        </TooltipTrigger>
                        <TooltipContent>
                            <p>Click for more details</p>
                        </TooltipContent>
                    </Tooltip>
                </TooltipProvider>
            </div>
        </div>
    </div>
</template>
