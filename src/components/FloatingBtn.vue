<template>
  <v-card id="create">
    <v-speed-dial
      v-model="fab"
      :top="top"
      :bottom="bottom"
      :right="right"
      :left="left"
      :direction="direction"
      :open-on-hover="hover"
      :transition="transition"
    >
      <template v-slot:activator>
        <v-btn v-model="fab" color="blue darken-2" dark fab>
          <v-icon v-if="fab"> mdi-close </v-icon>
          <v-icon v-else> mdi-account-circle </v-icon>
        </v-btn>
      </template>
      <v-btn fab dark small color="green" @click="$emit('open-dialog', true)">
        <v-icon>mdi mdi-pencil</v-icon>
      </v-btn>
      <v-btn
        fab
        dark
        small
        color="indigo"
        @click="$emit('open-file-upload-diaload', true)"
      >
        <v-icon>mdi-plus</v-icon>
      </v-btn>
      <v-btn fab dark small color="red">
        <v-icon>mdi-arrow-right</v-icon>
      </v-btn>
    </v-speed-dial>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    direction: "top",
    fab: true,
    fling: false,
    hover: true,
    top: false,
    right: true,
    bottom: true,
    left: false,
    transition: "slide-y-reverse-transition",
  }),

  computed: {},

  watch: {
    top(val) {
      this.bottom = !val;
    },
    right(val) {
      this.left = !val;
    },
    bottom(val) {
      this.top = !val;
    },
    left(val) {
      this.right = !val;
    },
  },
};
</script>

<style scoped>
#create .v-speed-dial {
  position: fixed;
}

#create .v-btn--floating {
  position: relative;
}
</style>