<script setup lang="ts">
import { GalleryVerticalEnd } from 'lucide-vue-next'

import {
  Sidebar,
  SidebarContent,
  SidebarGroup,
  SidebarHeader,
  SidebarMenu,
  SidebarMenuButton,
  SidebarMenuItem,
  SidebarMenuSub,
  SidebarMenuSubButton,
  SidebarMenuSubItem,
  type SidebarProps,
  SidebarRail,
} from '@/components/ui/sidebar'

const props = defineProps<SidebarProps>()
const login = ref(true)
// This is sample data.
const data = {
  navMain: [
    {
      title: 'Home',
      url: '/',
      items: [
        {
          title: 'Beranda',
          url: '/',
        },
        {
          title: 'Tentang Rekber',
          url: '/about',
        },
        {
          title: 'Cara Kerja',
          url: '/how-it-works',
        },
      ],
    },
    {
      title: 'Marketplace',
      url: '/products',
      items: [
        {
          title: 'Semua Produk',
          url: '/products',
        },
        {
          title: 'Kategori',
          url: '/categories',
        },
        {
          title: 'Produk Terbaru',
          url: '/products/latest',
        },
        {
          title: 'Produk Populer',
          url: '/products/popular',
        },
      ],
    },
    {
      title: 'Transaksi',
      url: '/orders',
      items: [
        {
          title: 'Pesanan Saya',
          url: '/orders',
          isActive: true,
        },
        {
          title: 'Riwayat Transaksi',
          url: '/transactions',
        },
        {
          title: 'Status Pembayaran',
          url: '/payments',
        },
      ],
    },
    {
      title: 'Toko Saya',
      url: '/seller',
      items: [
        {
          title: 'Dashboard',
          url: '/seller/dashboard',
        },
        {
          title: 'Kelola Produk',
          url: '/seller/products',
        },
        {
          title: 'Tambah Produk',
          url: '/seller/products/create',
        },
        {
          title: 'Pesanan Masuk',
          url: '/seller/orders',
        },
        {
          title: 'Saldo & Penarikan',
          url: '/seller/balance',
        },
        {
          title: 'Laporan Penjualan',
          url: '/seller/reports',
        },
      ],
    },
    {
      title: 'Chat',
      url: '/chat',
      items: [
        {
          title: 'Pesan Masuk',
          url: '/chat',
        },
        {
          title: 'Riwayat Chat',
          url: '/chat/history',
        },
      ],
    },
    {
      title: 'Akun',
      url: '/profile',
      items: [
        {
          title: 'Profil Saya',
          url: '/profile',
        },
        {
          title: 'Edit Profil',
          url: '/profile/edit',
        },
        {
          title: 'Keamanan',
          url: '/profile/security',
        },
        {
          title: 'Informasi Bank',
          url: '/profile/bank',
        },
        {
          title: 'Pengaturan',
          url: '/settings',
        },
      ],
    },
    {
      title: 'Bantuan',
      url: '/help',
      items: [
        {
          title: 'FAQ',
          url: '/help/faq',
        },
        {
          title: 'Panduan Lengkap',
          url: '/help/guide',
        },
        {
          title: 'Kontak Support',
          url: '/help/contact',
        },
        {
          title: 'Syarat & Ketentuan',
          url: '/help/terms',
        },
      ],
    },
  ],
}
</script>

<template>
  <Sidebar v-bind="props">
    <SidebarHeader>
      <SidebarMenu>
        <SidebarMenuItem>
          <SidebarMenuButton size="lg" as-child>
            <NuxtLink to="#">
              <div class="flex aspect-square size-8 items-center justify-center rounded-lg bg-sidebar-primary text-sidebar-primary-foreground">
                <h1>NR</h1>
              </div>
              <div class="flex flex-col gap-0.5 leading-none">
                <span class="font-medium">NUREK</span>
                <span class="">Nusovate Rekber</span>
              </div>
            </NuxtLink>
          </SidebarMenuButton>
        </SidebarMenuItem>
        <SidebarMenuItem class="flex flex-col gap-4 mt-12">
          <div class="h-fit w-full">
            <div class="h-24 w-24 overflow-hidden rounded-full bg-gray-200 mx-auto">
              <img src="" alt="avatar" class="w-full h-full">
            </div>
          </div>
          <SidebarMenuButton size="lg" as-child>
            <Button v-if="login" class="w-full mx-auto text-center cursor-pointer h-10 px-12 py-2 bg-transparent border border-red-200 text-red-500 hover:text-red-600 hover:bg-red-200">
              Logout
            </Button>
            <Button v-else class="w-full mx-auto text-center cursor-pointer h-10 px-12 py-2 bg-transparent border border-gray-300 text-gray-600 hover:text-gray-700 hover:bg-gray-200">
              Login
            </Button>
          </SidebarMenuButton>
        </SidebarMenuItem>
      </SidebarMenu>
    </SidebarHeader>
    <SidebarContent>
      <SidebarGroup>
        <SidebarMenu>
          <SidebarMenuItem v-for="item in data?.navMain" :key="item?.title">
            <SidebarMenuButton as-child>
              <NuxtLink :to="item?.url" class="font-medium">
                {{ item?.title }}
              </NuxtLink>
            </SidebarMenuButton>
            <SidebarMenuSub v-if="item?.items?.length">
              <SidebarMenuSubItem v-for="childItem in item?.items" :key="childItem?.title">
                <SidebarMenuSubButton as-child :is-active="childItem?.isActive">
                  <NuxtLink :to="childItem?.url">{{ childItem?.title }}</NuxtLink>
                </SidebarMenuSubButton>
              </SidebarMenuSubItem>
            </SidebarMenuSub>
          </SidebarMenuItem>
        </SidebarMenu>
      </SidebarGroup>
    </SidebarContent>
    <SidebarRail />
  </Sidebar>
</template>
