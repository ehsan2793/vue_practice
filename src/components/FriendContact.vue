<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(favorite)' : '' }}</h2>
    <button @click="toggleDetails">Show Details</button>
    <button @click="makeFavorite">Show Details</button>
    <ul v-if="details">
      <li><strong>Phone:</strong> {{ phone }}</li>
      <li><strong>Email:</strong> {{ email }}</li>
    </ul>
    <button @click="$emit('delete-friend',id)">Delete</button>
  </li>
</template>

<script>
export default {
  // props:["name" , "phone" , "email"],
  props: {
    id: { type: Number, required: true },
    name: { type: String, required: true },
    phone: { type: String, required: true },
    email: String,
    isFavorite: Boolean,
  },
  emits: ['toggle-favorite', 'delete-friend'],
  // emits: {
  // 'toggle-favorite': function (id) {
  //     if (id) {
  //         return true
  //     }else {
  //         console.warn("id is missing ");
  //         return false
  //     }
  // }
  // },
  data() {
    return {
      details: false,
    };
  },
  methods: {
    toggleDetails() {
      this.details = !this.details;
    },
    makeFavorite() {
      this.$emit('toggle-favorite', this.id);
    },

  },
};
</script>
