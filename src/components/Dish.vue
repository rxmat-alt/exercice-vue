<template>
  <q-card class="card">
    <q-img :src="dish.image" basic contain>
      <div class="absolute-bottom text-h6">
        {{ dish.nom }}
      </div>
    </q-img>

    <q-card-section>
      <q-rating
        :value="dish.note"
        size="2em"
        color="orange"
        readonly
        class="q-mt-sm"
      />
    </q-card-section>

    <q-card-section>
      {{ dish.description }}
    </q-card-section>

    <q-card-actions class="absolute-bottom" align="right">
      <q-btn @click="showFormDish = true" icon="edit" color="blue" flat
        >Modifier</q-btn
      >
      <q-btn icon="delete" color="red" flat>Supprimer</q-btn>
    </q-card-actions>

    <q-dialog v-model="showFormDish">
      <form-dish action="modifier" />
    </q-dialog>
  </q-card>
</template>

<script>
export default {
  props: ["dish"],
  data() {
    return {
      showFormDish: false,
    };
  },
  components: {
    "form-dish": require("components/FormDish.vue").default,
  },
};
</script>

<style>
.card {
  min-height: 400px;
  max-width: 250px;
  width: 250px;
  transition: background 0.3s;
}
.card-clickable {
  cursor: pointer;
}
.card-clickable:hover {
  background: #bdbdbd !important;
}
.card .q-img {
  max-height: 180px;
}
.card .q-img__image {
  background-size: cover !important;
}
.card .q-rating__icon {
  opacity: 0.2;
}
.card .q-rating__icon--active {
  opacity: 1;
}
</style>
