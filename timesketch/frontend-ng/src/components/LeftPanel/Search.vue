<!--
Copyright 2023 Google Inc. All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->
<template>
  <div>
    <router-link
      :to="{ name: 'Explore', params: { sketchId: sketch.id } }"
      custom
      v-slot="{ navigate }"
      class="pa-4"
      :class="
        $vuetify.theme.dark
          ? isExploreRoute
            ? 'dark-highlight'
            : 'dark-hover'
          : isExploreRoute
          ? 'light-highlight'
          : 'light-hover'
      "
      style="cursor: pointer"
    >
      <div @click="navigate" @keypress.enter="navigate" role="link"><v-icon left>mdi-magnify</v-icon> Search</div>
    </router-link>
    <v-divider></v-divider>
  </div>
</template>

<script>
export default {
  computed: {
    sketch() {
      return this.$store.state.sketch
    },
    isExploreRoute() {
      return this.$route.name === 'Explore'
    },
    sketchId() {
      return this.$store.state.sketch.id
    }
  },
}
</script>

