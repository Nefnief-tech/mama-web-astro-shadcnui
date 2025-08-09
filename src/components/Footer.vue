<script setup>
import { Heart, Github, Twitter } from 'lucide-vue-next'
</script>

<template>
  <footer class="bg-muted/50 border-t border-border/40 mt-20">
    <div class="container max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <!-- Brand Section -->
        <div class="col-span-1">
          <div class="text-2xl font-bold text-primary mb-4">
            💝 Mama's Website
          </div>
          <p class="text-muted-foreground text-sm">
            A beautiful website built with love using Astro.js and shadcn-vue components.
          </p>
        </div>

        <!-- Quick Links -->
        <div class="col-span-1">
          <h3 class="font-semibold text-foreground mb-4">Quick Links</h3>
          <ul class="space-y-2">
            <li>
              <a href="/" class="text-muted-foreground hover:text-foreground transition-colors text-sm">
                Home
              </a>
            </li>
            <li>
              <a href="/about" class="text-muted-foreground hover:text-foreground transition-colors text-sm">
                About
              </a>
            </li>
            <li>
              <a href="/contact" class="text-muted-foreground hover:text-foreground transition-colors text-sm">
                Contact
              </a>
            </li>
          </ul>
        </div>

        <!-- Tech Stack -->
        <div class="col-span-1">
          <h3 class="font-semibold text-foreground mb-4">Built With</h3>
          <ul class="space-y-2 text-sm text-muted-foreground">
            <li>🚀 Astro.js</li>
            <li>💚 Vue.js</li>
            <li>🎨 shadcn-vue</li>
            <li>🌈 Tailwind CSS</li>
          </ul>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div class="border-t border-border/40 mt-8 pt-8 flex flex-col sm:flex-row justify-between items-center">
        <div class="text-muted-foreground text-sm flex items-center">
          Made with <Heart class="h-4 w-4 mx-1 text-red-500" /> for Mama
        </div>
        <div class="text-muted-foreground text-sm mt-4 sm:mt-0">
          © 2024 Mama's Website. All rights reserved.
        </div>
      </div>
    </div>
  </footer>
</template>