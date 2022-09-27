<template>
  <v-container>
    <v-row align="center" justify="center" class="ma-4">
      <v-col cols="12" md="4">
        <v-select
          v-model="filterByCountryValue"
          :items="filterByCountryItems"
          clearable
          label="Filter by country"
        ></v-select>

        <v-select
          v-model="filterByScoreValue"
          :items="filterByScoreItems"
          clearable
          label="Filter by score"
        ></v-select>
      </v-col>

      <v-col cols="12" md="4">
        <v-card max-width="450" class="mx-auto">
          <v-list three-line>
            <ListItem
              v-for="(item, index) in filteredUsers"
              :key="index"
              :user="item"
            />
          </v-list>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { User } from "@/types/User";
import ListItem from "./ListItem.vue";

export default defineComponent({
  name: "ContentBlock",
  components: {
    ListItem,
  },
  data: () => ({
    filterByCountryItems: ["russia", "usa"],
    filterByScoreItems: ["> 20", "< 10"],
    filterByCountryValue: "",
    filterByScoreValue: "",
    users: [
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/1.jpg",
        title: "Brunch this weekend?",
        subtitle: `<span class="text--primary">Ali Connors</span> &mdash; I'll be in your neighborhood doing errands this weekend. Do you want to hang out?`,
        country: "Russia",
        score: 2,
        header: "List",
      },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
        title: 'Summer BBQ <span class="grey--text text--lighten-1">4</span>',
        subtitle: `<span class="text--primary">to Alex, Scott, Jennifer</span> &mdash; Wish I could come, but I'm out of town this weekend.`,
        country: "France",
        score: 3,
        divider: true,
        inset: false,
      },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/3.jpg",
        title: "Oui oui",
        subtitle:
          '<span class="text--primary">Sandra Adams</span> &mdash; Do you have Paris recommendations? Have you ever been?',
        country: "Russia",
        score: 22,
        divider: false,
        inset: true,
      },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/4.jpg",
        title: "Birthday gift",
        subtitle:
          '<span class="text--primary">Trevor Hansen</span> &mdash; Have any ideas about what we should get Heidi for her birthday?',
        country: "China",
        score: 32,
        divider: false,
        inset: true,
      },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/5.jpg",
        title: "Recipe to try",
        subtitle:
          '<span class="text--primary">Britta Holt</span> &mdash; We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
        country: "India",
        score: 22,
        divider: true,
        inset: true,
      },
    ] as User[],
  }),
  computed: {
    filteredUsers() {
      return this.users.filter((user) => {
        const filteredByCountry = this.filterByCountryValue
          ? user.country.toLowerCase() ===
            this.filterByCountryValue.toLowerCase()
          : true;
        let filteredByScore = true;
        if (this.filterByScoreValue) {
          if (this.filterByScoreValue === "> 20" && user.score <= 20) {
            filteredByScore = false;
          }
          if (this.filterByScoreValue === "< 10" && user.score >= 10) {
            filteredByScore = false;
          }
        }
        return filteredByCountry && filteredByScore;
      });
    },
  },
});
</script>
