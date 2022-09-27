<template>
  <v-app>
    <v-main>
      <ContentBlock />
    </v-main>

    <v-footer app v-bind="localAttrs">
      <AppFooter />
    </v-footer>
  </v-app>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ContentBlock from "./components/ContentBlock.vue";
import AppFooter from "./components/AppFooter.vue";

export default defineComponent({
  name: "App",
  components: {
    ContentBlock,
    AppFooter,
  },
  computed: {
    localAttrs() {
      const attrs = {
        absolute: true,
        fixed: false,
      };
      return attrs;
    },
  },
  data: () => ({
    //
  }),
});
</script>
