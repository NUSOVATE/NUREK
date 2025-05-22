<script setup lang="ts">
import AppSidebar from '~/components/AppSidebar.vue'
import {
  Breadcrumb,
  BreadcrumbItem,
  BreadcrumbLink,
  BreadcrumbList,
  BreadcrumbPage,
  BreadcrumbSeparator,
} from '~/components/ui/breadcrumb'
import {Separator} from '~/components/ui/separator'
import {
  SidebarInset, SidebarMenuButton,
  SidebarProvider,
  SidebarTrigger,
} from '~/components/ui/sidebar'

const position = computed(() => useRoute().fullPath)

const postionPage = computed(() => {
  let cleanedPath = position.value.replace(/^\/|\/$/g, '');
  if (cleanedPath === '') {
    return null
  } else {
    return cleanedPath.split('/')[0]
  }
})
</script>

<template>
  <SidebarProvider>
    <client-only>
      <AppSidebar/>
    </client-only>
    <SidebarInset class="h-screen flex flex-col">
      <header class="flex h-16 shrink-0 items-center justify-between gap-2 border-b">
        <div class="flex items-center gap-2 px-3">
          <SidebarTrigger class="cursor-pointer"/>
          <Separator orientation="vertical" class="md:mr-2 h-4"/>
          <Breadcrumb>
            <BreadcrumbList>
              <BreadcrumbItem class="hidden md:block">
                <BreadcrumbLink href="/">
                  Home
                </BreadcrumbLink>
              </BreadcrumbItem>
              <BreadcrumbSeparator v-if="postionPage !== null" class="hidden md:block"/>
              <BreadcrumbItem v-if="postionPage !== null" class="hidden md:block">
                <BreadcrumbPage class="capitalize">{{ postionPage }}</BreadcrumbPage>
              </BreadcrumbItem>
              <SidebarMenuButton size="lg" as-child class="md:hidden">
                <NuxtLink to="/">
                  <div class="flex flex-col gap-0.5 leading-none">
                    <span class="font-medium">NUREK</span>
                    <span class="">Nusovate Rekber</span>
                  </div>
                </NuxtLink>
              </SidebarMenuButton>
            </BreadcrumbList>
          </Breadcrumb>
        </div>
        <div class="flex items-center gap-2 px-3">
          <div class="h-8 w-8 overflow-hidden rounded-full bg-gray-200 mx-auto">
            <img src="" alt="avatar" class="w-full h-full">
          </div>
        </div>
      </header>
      <main class="h-full">
        <slot/>
      </main>
    </SidebarInset>
  </SidebarProvider>
</template>