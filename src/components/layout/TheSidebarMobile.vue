<script setup lang="ts">
const isOpen = ref(false)
const navigation = useNavigationStore()
</script>

<template>
  <div class="absolute inset-y-0 left-1.5 flex items-center lg:hidden">
    <button type="button" class="relative" @click="isOpen = true">
      <span class="sr-only">Open navigation</span>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-7 w-7 stroke-slate-400"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
        stroke-width="2"
        aria-hidden="true"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M4 6h16M4 12h16M4 18h16"
        />
      </svg>
    </button>
  </div>

  <Dialog
    class="fixed inset-0 z-50 flex items-start overflow-y-auto bg-slate-900/50 pr-10 backdrop-blur lg:hidden"
    :open="isOpen"
    @close="isOpen = false"
  >
    <DialogPanel
      class="min-h-full w-full max-w-xs bg-white px-4 pt-5 pb-12 dark:bg-slate-900 sm:px-6"
    >
      <DialogTitle class="sr-only">Navigation</DialogTitle>
      <div class="flex items-center">
        <button type="button" @click="isOpen = false">
          <span class="sr-only">Close navigation</span>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6 stroke-slate-400"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
            aria-hidden="true"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>
      <nav class="mt-10">
        <nav>
          <the-sidebar-navigation
            :navigation="navigation.mainNavigation"
            section-name="Introduction"
          />

          <the-sidebar-navigation
            :navigation="navigation.cheatsheetNavigation"
            section-name="Cheatsheet"
          />

          <the-sidebar-navigation
            :navigation="navigation.standardLibraryNavigation"
            section-name="Standard Library"
          />
        </nav>
      </nav>
    </DialogPanel>
  </Dialog>
</template>
