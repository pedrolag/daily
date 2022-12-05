<script setup>
const squad = ref([
  {
    name: "Bruno Rovela",
    image:
      "https://plataformaamais.atlassian.net/wiki/aa-avatar/5c06d6f510c30e4ac8c8d0fe",
  },
  {
    name: "Eder Sena",
    image:
      "https://plataformaamais.atlassian.net/wiki/aa-avatar/628f7ddc1a437e00704370f1",
  },
  {
    name: "Nicolas Gross",
    image:
      "https://plataformaamais.atlassian.net/wiki/aa-avatar/620a81c9eb29780068909ded",
  },
  {
    name: "Pedro Gonçalves",
    image:
      "https://plataformaamais.atlassian.net/wiki/aa-avatar/614224581238e8007133d470",
  },
  {
    name: "Thiago Tinoco",
    image:
      "https://plataformaamais.atlassian.net/wiki/aa-avatar/5fe0dad844065f013f160051",
  },
  {
    name: "Vitor Duggen",
    image:
      "https://plataformaamais.atlassian.net/wiki/aa-avatar/61eafe2438041c0068809493",
  },
]);

const shuffle = (list) => {
  return useShuffle(list);
};
</script>

<template>
  <div
    class="main container mx-auto h-full flex flex-col items-center justify-center gap-8"
  >
    <div
      class="relative flex flex-row items-center justify-between gap-4 max-w-3xl"
    >
      <TransitionGroup name="fade">
        <div class="avatar" v-for="member in squad" :key="member.name">
          <div class="w-24 mask mask-squircle">
            <img :src="member.image" />
          </div>
        </div>
      </TransitionGroup>
    </div>

    <button class="btn" @click="squad = shuffle(squad)">shuffle</button>
  </div>
</template>

<style lang="postcss">
html,
body,
#__nuxt,
.main {
  @apply h-full;
}

/* 1. declare transition */
.fade-move,
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s cubic-bezier(0.55, 0, 0.1, 1);
}

/* 2. declare enter from and leave to state */
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: scaleY(0.01) translate(30px, 0);
}

/* 3. ensure leaving items are taken out of layout flow so that moving
      animations can be calculated correctly. */
.fade-leave-active {
  position: absolute;
}
</style>
