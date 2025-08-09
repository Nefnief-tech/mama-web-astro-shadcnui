<script setup>
import { Button } from '@/components/ui/button'
import { Menu, X, Home, Heart, Mail } from 'lucide-vue-next'
import { ref } from 'vue'

const isOpen = ref(false)

const toggleMenu = () => {
  isOpen.value = !isOpen.value
}

const menuItems = [
  { href: '/', label: 'Home', icon: Home },
  { href: '/about', label: 'About', icon: Heart },
  { href: '/contact', label: 'Contact', icon: Mail }
]
</script>

<template>
  <nav class="bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60 sticky top-0 z-50 w-full border-b border-border/40">
    <div class="container max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <!-- Logo/Brand -->
        <div class="flex-shrink-0">
          <a href="/" class="text-2xl font-bold text-primary">
            💝 Mama's Website
          </a>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:block">
          <div class="ml-10 flex items-baseline space-x-4">
            <a 
              v-for="item in menuItems" 
              :key="item.href"
              :href="item.href" 
              class="text-muted-foreground hover:text-foreground transition-colors px-3 py-2 rounded-md text-sm font-medium"
            >
              {{ item.label }}
            </a>
          </div>
        </div>

        <!-- Mobile menu button -->
        <div class="md:hidden">
          <Button 
            variant="ghost" 
            size="icon"
            @click="toggleMenu"
            aria-label="Toggle menu"
          >
            <Menu v-if="!isOpen" class="h-6 w-6" />
            <X v-else class="h-6 w-6" />
          </Button>
        </div>
      </div>

      <!-- Mobile Navigation -->
      <div v-if="isOpen" class="md:hidden">
        <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
          <a 
            v-for="item in menuItems" 
            :key="item.href"
            :href="item.href" 
            class="text-muted-foreground hover:text-foreground transition-colors block px-3 py-2 rounded-md text-base font-medium"
            @click="isOpen = false"
          >
            <component :is="item.icon" class="inline h-4 w-4 mr-2" />
            {{ item.label }}
          </a>
        </div>
      </div>
    </div>
  </nav>
</template>