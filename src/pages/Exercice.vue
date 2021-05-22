<template>
  <q-page class="q-pa-lg">
    <q-pull-to-refresh @refresh="refresh">
      <div class="row q-gutter-lg">
        <dishe v-for="dishe in dishes" :key="dishe.id" :dishe="dishe" />

        <add-button @click="showFormDishe = true" />

        <q-dialog v-model="showFormDishe">
          <form-dishe action="add" />
        </q-dialog>
      </div>
      <div class="q-pa-md scroll" style="height: 300px">
        <q-pull-to-refresh @refresh="refresh">
          <div v-for="(item, index) in items" :key="index" class="q-mb-sm">
            <q-badge color="secondary">
              {{ items.length - index }}
            </q-badge>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
          </div>
        </q-pull-to-refresh>
      </div>
    </q-pull-to-refresh>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      showFormDishe: false
    }
  },
  computed: {
    dishes () {
      return this.$store.getters.dishes;
    }
  },
  components: {
    dishe: require("components/Dishe.vue").default,
    "add-button": require("components/AddButton.vue").default,
    "form-dishe": require("components/FormDishe.vue").default
  },
  methods: {
    refresh (done) {
      // Do stuff to retrieve data
      setTimeout(() => {
        done();
      }, 1000)
    }
  }
};
</script>
