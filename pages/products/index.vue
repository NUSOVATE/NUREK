<template>
  <div class="grid grid-cols-1 lg:grid-cols-3 h-full">
    <div class="p-4 flex flex-col gap-5 border-r">
      <div class="flex flex-col gap-0.5 leading-none">
        <span class="font-medium">MARKETPLACE</span>
      </div>
      <div class="relative w-full items-center">
        <Input id="search" type="text" placeholder="Search..." class="pl-10"/>
        <span class="absolute start-0 inset-y-0 flex items-center justify-center px-2">
          <Search class="size-6 text-muted-foreground"/>
        </span>
      </div>
      <div class="grid-cols-1 gap-2" :class="isHistory ? 'grid' : 'hidden lg:grid'">
        <div class="flex items-center justify-between text-gray-600 p-2">
          <span class="font-medium text-sm">Recent</span>
          <span class="text-sm">X</span>
        </div>
        <div v-for="i in [1,2,3,4,5,6]" :key="i" class="flex items-center justify-between p-2 cursor-pointer hover:bg-gray-100">
          <span class="text-gray-500 text-sm">Lorem ipsum dolor sit amet {{ i }}.</span>
          <span class="text-gray-600 text-sm">X</span>
        </div>
      </div>
    </div>
    <div class="p-4 col-span-2 w-full h-full overflow-y-auto">
      <h2 class="text-xl font-medium leading-none">Products</h2>
      <div class="grid grid-cols-2 gap-4 xl:grid-cols-3 mt-4">
        <Card v-for="i in [1,2,3,4,5,6,7,8,9,10]" :key="i" class="group h-80 cursor-pointer shadow-none border-none grid grid-rows-9 p-0 overflow-hidden rounded-lg">
          <CardHeader class="row-span-6 h-full w-full overflow-hidden p-0">
            <img src="https://www.eurobridge.in/images/product-06.jpg" alt="Cover" class="object-cover object-center">
          </CardHeader>
          <CardContent class="row-span-3 p-4 gap-2 group-hover:underline">
            <CardTitle>RP. 179.000</CardTitle>
            <CardDescription class="text-gray-900">Iphone 14plus 128gb lock</CardDescription>
            <CardFooter class="p-0 text-gray-600 font-medium text-xs mt-2">
              banyumas
            </CardFooter>
          </CardContent>
        </Card>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import {Search} from 'lucide-vue-next'
import {Input} from '@/components/ui/input'

const isHistory = ref(false)
</script>

<style scoped>

</style>