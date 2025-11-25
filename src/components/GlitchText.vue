<template>
  <div class="glitch" :data-text="text">{{ text }}</div>
</template>

<script lang="ts" setup>
defineProps<{ text: string }>()
</script>

<style scoped>
.glitch {
  position: relative;
  font-size: 3rem;
  color: white;
  font-weight: bold;
  text-transform: uppercase;
  animation: glitch 2s infinite;
}

.glitch::before,
.glitch::after {
  content: attr(data-text);
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
}

.glitch::before {
  text-shadow: -2px 0 red;
  animation: glitchTop 1.8s infinite;
}

.glitch::after {
  text-shadow: -2px 0 cyan;
  animation: glitchBottom 1.8s infinite;
}

/* Fő glitch animáció */
@keyframes glitch {
  0% { transform: none; }
  20% { transform: skew(-0.5deg, -0.9deg); }
  40% { transform: skew(0.9deg, 0.2deg); }
  60% { transform: skew(-1deg, 0.4deg); }
  80% { transform: skew(0.4deg, -0.1deg); }
  100% { transform: none; }
}

/* Felső csúszó glitch */
@keyframes glitchTop {
  0% { clip-path: inset(0 0 60% 0); transform: translate(0); }
  33% { clip-path: inset(0 0 60% 0); transform: translate(-2px, -2px); }
  66% { clip-path: inset(0 0 60% 0); transform: translate(2px, 2px); }
  100% { clip-path: inset(0 0 60% 0); transform: translate(0); }
}

/* Alsó csúszó glitch */
@keyframes glitchBottom {
  0% { clip-path: inset(40% 0 0 0); transform: translate(0); }
  33% { clip-path: inset(40% 0 0 0); transform: translate(2px, 2px); }
  66% { clip-path: inset(40% 0 0 0); transform: translate(-2px, -2px); }
  100% { clip-path: inset(40% 0 0 0); transform: translate(0); }
}
</style>
