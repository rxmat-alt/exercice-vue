<template>
  <q-page class="q-pa-lg">
    <div class="row q-gutter-lg">
      <dish v-for="dish in dishes" :key="dish.id" :dish="dish" />

      <add-button @click="showFormDish = true" />

      <q-dialog v-model="showFormDish">
        <form-dish action="add" />
      </q-dialog>
    </div>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      dishes: [
        {
          id: 1,
          image: "https://i.imgur.com/0umadnY.jpg",
          nom: "Burger",
          description:
            "Un hamburger est un sandwich composé d'une ou plusieurs tranches de viande hachée, généralement du bœuf, placées dans un petit pain ou une brioche.",
          note: 4
        },
        {
          id: 2,
          image: "https://i.imgur.com/b9zDbyb.jpg",
          nom: "Pizza",
          description:
            "La pizza est un plat savoureux d'origine italienne, consistant en une base généralement ronde et aplatie de pâte levée à base de blé.",
          note: 5
        },
        {
          id: 3,
          image: "https://i.imgur.com/RbKjUjB.jpg",
          nom: "Petits choux",
          description:
            "Le chou de Bruxelles est une variété de chou, plante herbacée de la famille des Brassicaceae. C’est vraiement pas bon...",
          note: 1
        },
        {
          id: 4,
          image: "https://i.imgur.com/xAuhNVg.jpg",
          nom: "BBQ Ribs",
          description:
            "Les BBQ ribs ou barbecue ribs sont des grands classiques très appréciés partout dans le monde.",
          note: 5
        }
      ],
      showFormDish: false
    };
  },
  components: {
    dish: require("components/Dish.vue").default,
    "add-button": require("components/AddButton.vue").default,
    "form-dish": require("components/FormDish.vue").default
  }
};
</script>
