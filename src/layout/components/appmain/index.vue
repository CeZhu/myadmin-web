<template>
  <div id="app-main">
    <router-view v-slot="{ Component }">
      <transition
        name="fade"
        enter-active-class="animated swing"
        leave-active-class="animated shake"
        mode="out-in"
      >
        <keep-alive>
          <component :is="Component" />
        </keep-alive>
      </transition>
    </router-view>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from "vue";
import { useRoute } from "vue-router";
export default defineComponent({
  setup() {
    const route = useRoute();
    const key = computed(() => route.path);
    return {
      key,
    };
  },
});
</script>

<style scoped>
#app-main {
  position: absolute;
  left: 220px;
  top: 0;
  width: 85%;
}
</style>
