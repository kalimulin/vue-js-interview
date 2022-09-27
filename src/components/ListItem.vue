<template>
  <v-divider v-if="user.divider" :inset="user.inset"></v-divider>

  <v-list-item>
    <v-avatar>
      <v-img :src="user.avatar"></v-img>
    </v-avatar>

    <v-list-item-media>
      <v-list-item-title v-html="user.title"></v-list-item-title>
      <v-list-item-subtitle v-html="user.subtitle"></v-list-item-subtitle>
    </v-list-item-media>
  </v-list-item>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { User } from "../types/User";

export default defineComponent({
  name: "ListItem",
  props: {
    user: {
      required: true,
      type: Object as () => User,
    },
  },
});
</script>
