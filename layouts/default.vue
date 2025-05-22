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
  SidebarInset,
  SidebarProvider,
  SidebarTrigger,
} from '~/components/ui/sidebar'

const position = computed(() => useRoute().fullPath)

const postionPage = computed(() => {
  let cleanedPath = position.value.replace(/^\/|\/$/g, '');
  if(cleanedPath === '') {
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
    <SidebarInset>
      <header class="flex h-16 shrink-0 items-center gap-2 border-b">
        <div class="flex items-center gap-2 px-3">
          <SidebarTrigger class="cursor-pointer" />
          <Separator orientation="vertical" class="mr-2 h-4"/>
          <Breadcrumb>
            <BreadcrumbList>
              <BreadcrumbItem class="hidden md:block">
                <BreadcrumbLink href="/">
                  Home
                </BreadcrumbLink>
              </BreadcrumbItem>
              <BreadcrumbSeparator v-if="postionPage !== null" class="hidden md:block"/>
              <BreadcrumbItem v-if="postionPage !== null">
                <BreadcrumbPage class="capitalize">{{ postionPage }}</BreadcrumbPage>
              </BreadcrumbItem>
            </BreadcrumbList>
          </Breadcrumb>
        </div>
      </header>
      <main>
        <slot/>
      </main>
    </SidebarInset>
  </SidebarProvider>
</template>