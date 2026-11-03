<script setup lang="ts">
definePageMeta({
  // layout: 'site',
})

const faqValue = ref<string[]>([])
</script>

<template>
  <div class="min-h-screen text-primary bg-background">
    <!-- Header Navigation -->
    <header class="sticky top-0 z-50 w-full bg-background/90 backdrop-blur border-b border-border">
      <nav class="container mx-auto px-4 py-4 flex items-center justify-between max-w-7xl">
        <div class="flex items-center gap-3">
          <div class="w-9 h-9 bg-primary rounded-lg flex items-center justify-center shadow-lg">
            <span class="text-background font-black text-2xl tracking-tight">K</span>
          </div>
          <span class="text-2xl font-extrabold tracking-tight text-primary">Konvert</span>
        </div>

        <div class="hidden md:flex items-center gap-8">
          <a href="#home" class="text-primary font-medium hover:text-primary/80 transition-colors">Home</a>
          <a href="#about" class="text-muted-foreground font-medium hover:text-primary transition-colors">About</a>
          <a href="#services" class="text-muted-foreground font-medium hover:text-primary transition-colors">Services</a>
          <a href="#contact" class="text-muted-foreground font-medium hover:text-primary transition-colors">Contact</a>
        </div>

        <div class="flex items-center gap-2">
          <UButton variant="outline" class="border-primary text-primary hover:bg-primary hover:text-background focus:ring-2 focus:ring-primary/50 px-6 py-2 font-semibold transition-all rounded-md">
            Sign Up
          </UButton>
          <ModeToggle />
        </div>
      </nav>
    </header>

    <!-- Hero Section -->
    <section id="home" class="container mx-auto px-4 py-24 max-w-7xl">
      <div class="grid md:grid-cols-2 gap-16 items-center">
        <div class="space-y-7">
          <div class="flex items-center gap-3">
            <div class="flex gap-0.5">
              <Icon name="material-symbols:star-rounded" class="text-primary text-xl" />
              <Icon name="material-symbols:star-rounded" class="text-primary text-xl" />
              <Icon name="material-symbols:star-rounded" class="text-primary text-xl" />
              <Icon name="material-symbols:star-rounded" class="text-primary text-xl" />
              <Icon name="material-symbols:star-rounded" class="text-primary text-xl" />
            </div>
            <span class="text-primary font-semibold text-base">5.0/5.0</span>
          </div>

          <h1 class="text-6xl md:text-7xl font-extrabold text-primary tracking-tight leading-tight mb-2">
            A Simple Headline
          </h1>

          <p class="text-muted-foreground text-lg leading-relaxed font-light mb-4">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation.
          </p>

          <div class="flex flex-col sm:flex-row gap-4 w-full">
            <UButton
              class="bg-gradient-to-tr from-primary to-secondary hover:from-primary/80 hover:to-secondary/80 text-background px-10 py-6 text-lg rounded-xl font-semibold shadow-md transform active:scale-95 flex items-center gap-2"
            >
              CALL TO ACTION BUTTON
              <Icon name="material-symbols:arrow-forward-rounded" class="text-xl" />
            </UButton>
            <UButton
              variant="outline"
              class="border-primary text-primary hover:bg-primary hover:text-background px-10 py-6 text-lg rounded-xl font-semibold transition-all"
            >
              Learn More
            </UButton>
          </div>
        </div>

        <div class="bg-card rounded-2xl p-8 border border-border h-96 flex items-center justify-center shadow-inner">
          <span class="text-muted-foreground text-2xl opacity-70">Image Placeholder</span>
        </div>
      </div>
    </section>

    <!-- Client Logos -->
    <section class="container mx-auto px-4 py-12 max-w-7xl">
      <div class="grid grid-cols-2 md:grid-cols-5 gap-4">
        <div
          v-for="i in 5"
          :key="i"
          class="bg-card/80 rounded-xl p-6 border border-border flex items-center justify-center gap-2 shadow"
        >
          <Icon name="material-symbols:shield-rounded" class="text-muted text-xl" />
          <span class="text-muted-foreground font-semibold">Logolpsum</span>
        </div>
      </div>
    </section>

    <!-- Benefits Section -->
    <section id="about" class="container mx-auto px-4 py-20 max-w-7xl">
      <h2 class="text-4xl font-extrabold text-center mb-12 tracking-tight text-primary">
        Benefits
      </h2>
      <div class="grid md:grid-cols-3 gap-8">
        <UCard
          v-for="i in 3"
          :key="i"
          class="bg-card border border-border rounded-2xl shadow"
        >
          <UCardHeader>
            <UCardTitle class="text-primary font-bold text-2xl">
              Benefit {{ i }}
            </UCardTitle>
          </UCardHeader>
          <UCardContent>
            <p class="text-muted-foreground font-light text-base">
              Description of benefit goes here.
            </p>
          </UCardContent>
        </UCard>
      </div>
    </section>

    <!-- Process Section -->
    <section class="container mx-auto px-4 py-20 max-w-7xl">
      <h2 class="text-4xl font-extrabold text-center mb-12 tracking-tight text-primary">
        Process Section
      </h2>
      <div class="grid md:grid-cols-3 gap-8">
        <UCard
          v-for="i in 3"
          :key="i"
          class="bg-card border border-border rounded-2xl shadow"
        >
          <UCardHeader>
            <div class="flex items-center gap-4">
              <div class="w-12 h-12 bg-primary rounded-full flex items-center justify-center text-background font-black text-2xl shadow">
                {{ i }}
              </div>
              <UCardTitle class="text-primary font-bold text-xl">
                Step {{ i }}
              </UCardTitle>
            </div>
          </UCardHeader>
          <UCardContent>
            <p class="text-muted-foreground font-light text-base">
              Process description goes here.
            </p>
          </UCardContent>
        </UCard>
      </div>
    </section>

    <!-- Features Section -->
    <section id="services" class="container mx-auto px-4 py-20 max-w-7xl">
      <h2 class="text-4xl font-extrabold text-center mb-12 tracking-tight text-primary">
        Features
      </h2>
      <div class="grid md:grid-cols-2 gap-8 mb-8">
        <UCard
          v-for="i in 2"
          :key="i"
          class="bg-card border border-border rounded-2xl shadow"
        >
          <UCardHeader>
            <UCardTitle class="text-primary font-bold text-xl">
              Feature {{ i }}
            </UCardTitle>
          </UCardHeader>
          <UCardContent>
            <p class="text-muted-foreground font-light text-base">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
            </p>
          </UCardContent>
        </UCard>
      </div>
      <div class="grid md:grid-cols-3 gap-8">
        <UCard
          v-for="i in 3"
          :key="i + 2"
          class="bg-card border border-border rounded-2xl shadow"
        >
          <UCardHeader>
            <UCardTitle class="text-primary font-bold text-xl">
              Feature {{ i + 2 }}
            </UCardTitle>
          </UCardHeader>
          <UCardContent>
            <p class="text-muted-foreground font-light text-base">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            </p>
          </UCardContent>
        </UCard>
      </div>
    </section>

    <!-- Pricing Section -->
    <section class="container mx-auto px-4 py-20 max-w-7xl">
      <h2 class="text-4xl font-extrabold text-center mb-12 tracking-tight text-primary">
        Pricing
      </h2>
      <div class="grid md:grid-cols-3 gap-8">
        <!-- Basic Plan -->
        <UCard class="bg-card border border-border rounded-2xl shadow">
          <UCardHeader>
            <div class="text-4xl font-black text-primary mb-2 tracking-tight">
              $28
            </div>
            <UCardTitle class="text-muted-foreground font-semibold text-xl">
              Basic
            </UCardTitle>
            <p class="text-muted text-sm mt-2">
              Best for personal projects and side-hustles.
            </p>
          </UCardHeader>
          <UCardContent class="space-y-4 mt-2">
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-primary" />
              <span class="text-muted-foreground">Feature 1</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-primary" />
              <span class="text-muted-foreground">Feature 2</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-primary" />
              <span class="text-muted-foreground">Feature 3</span>
            </div>
            <UButton
              variant="outline"
              class="w-full mt-6 border-primary text-primary hover:bg-primary hover:text-background font-semibold rounded-lg transition"
            >
              Start Free Trial
            </UButton>
          </UCardContent>
        </UCard>

        <!-- Pro Plan -->
        <UCard class="bg-card border border-border rounded-2xl shadow">
          <UCardHeader>
            <div class="text-4xl font-black text-primary mb-2 tracking-tight">
              $79
            </div>
            <UCardTitle class="text-muted-foreground font-semibold text-xl">
              Pro
            </UCardTitle>
            <p class="text-muted text-sm mt-2">
              Best for growing teams and small businesses.
            </p>
          </UCardHeader>
          <UCardContent class="space-y-4 mt-2">
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-primary" />
              <span class="text-muted-foreground">Feature 1</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-primary" />
              <span class="text-muted-foreground">Feature 2</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-primary" />
              <span class="text-muted-foreground">Feature 3</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-primary" />
              <span class="text-muted-foreground">Feature 4</span>
            </div>
            <UButton
              variant="outline"
              class="w-full mt-6 border-primary text-primary hover:bg-primary hover:text-background font-semibold rounded-lg transition"
            >
              Start Free Trial
            </UButton>
          </UCardContent>
        </UCard>

        <!-- Enterprise Plan (Highlighted) -->
        <UCard class="bg-gradient-to-tr from-primary via-primary to-secondary border-2 border-secondary rounded-2xl shadow-lg">
          <UCardHeader>
            <div class="text-4xl font-black text-background mb-2 tracking-tight">
              $149
            </div>
            <UCardTitle class="text-background font-bold text-xl">
              Enterprise
            </UCardTitle>
            <p class="text-secondary-foreground text-sm mt-2">
              Best for large teams and organizations.
            </p>
          </UCardHeader>
          <UCardContent class="space-y-4 mt-2">
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-background" />
              <span class="text-secondary-foreground">Feature 1</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-background" />
              <span class="text-secondary-foreground">Feature 2</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-background" />
              <span class="text-secondary-foreground">Feature 3</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-background" />
              <span class="text-secondary-foreground">Feature 4</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="material-symbols:check-rounded" class="text-background" />
              <span class="text-secondary-foreground">Feature 5</span>
            </div>
            <UButton
              class="w-full mt-6 bg-background text-secondary font-semibold flex items-center justify-center gap-2 py-4 rounded-lg hover:bg-secondary/10 transition"
            >
              GET STARTED NOW
              <Icon name="material-symbols:arrow-forward-rounded" />
            </UButton>
          </UCardContent>
        </UCard>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section class="container mx-auto px-4 py-20 max-w-7xl">
      <h2 class="text-4xl font-extrabold text-center mb-12 tracking-tight text-primary">
        Testimonials
      </h2>
      <div class="grid md:grid-cols-3 gap-8">
        <UCard
          v-for="i in 3"
          :key="i"
          class="bg-card border border-border rounded-2xl shadow"
        >
          <UCardContent class="pt-8 space-y-4">
            <div class="flex gap-1">
              <Icon
                v-for="star in 5"
                :key="star"
                name="material-symbols:star-rounded"
                class="text-primary text-xl"
              />
            </div>
            <p class="text-primary italic text-lg font-light">
              "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
            </p>
            <p class="text-primary/70 font-semibold text-base">
              John Doe
            </p>
          </UCardContent>
        </UCard>
      </div>
    </section>

    <!-- FAQ Section -->
    <section id="contact" class="container mx-auto px-4 py-20 max-w-7xl">
      <h2 class="text-4xl font-extrabold text-center mb-12 tracking-tight text-primary">
        FAQ
      </h2>
      <div class="max-w-3xl mx-auto">
        <UAccordion v-model="faqValue" collapsible class="space-y-4">
          <UAccordionItem
            v-for="i in 3"
            :key="i"
            :value="`item-${i}`"
            class="bg-card border border-border rounded-xl"
          >
            <UAccordionTrigger class="font-medium text-primary hover:text-primary/80 px-6 py-4 transition">
              Question Type Goes Here
            </UAccordionTrigger>
            <UAccordionContent class="px-6 pb-6 text-muted-foreground">
              Answer to the question goes here. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            </UAccordionContent>
          </UAccordionItem>
        </UAccordion>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="container mx-auto px-4 py-20 max-w-7xl">
      <div class="bg-card rounded-2xl p-14 border border-border text-center shadow-md">
        <h2 class="text-4xl font-extrabold mb-8 tracking-tight text-primary">
          CTA Section
        </h2>
        <UButton
          class="bg-gradient-to-tr from-primary to-secondary hover:from-primary/80 hover:to-secondary/80 text-background px-10 py-6 text-xl rounded-xl font-semibold shadow-md flex items-center gap-2 mx-auto"
        >
          CALL TO ACTION BUTTON
          <Icon name="material-symbols:arrow-forward-rounded" class="text-2xl" />
        </UButton>
      </div>
    </section>

    <!-- Footer -->
    <footer class="border-t border-border bg-background/90">
      <div class="container mx-auto px-4 py-14 max-w-7xl">
        <div class="flex flex-col md:flex-row items-center justify-between gap-8 mb-10">
          <div class="flex items-center gap-3">
            <div class="w-10 h-10 bg-primary rounded-lg flex items-center justify-center shadow">
              <span class="text-background font-black text-xl">K</span>
            </div>
            <span class="text-2xl font-extrabold tracking-tight text-primary">Konvert</span>
          </div>
          <p class="text-muted-foreground font-medium text-lg">
            Nothing Random
          </p>
        </div>

        <div class="flex flex-wrap justify-center gap-4 mb-8">
          <UButton
            v-for="social in ['Facebook', 'Twitter', 'Instagram', 'LinkedIn', 'YouTube', 'TikTok']"
            :key="social"
            variant="outline"
            class="border-border text-primary hover:bg-primary hover:text-background font-semibold rounded-xl px-6 py-2 transition"
          >
            {{ social }}
          </UButton>
        </div>

        <div class="text-center text-muted text-sm">
          © 2023 Konvert. All rights reserved.
        </div>
      </div>
    </footer>
  </div>
</template>
