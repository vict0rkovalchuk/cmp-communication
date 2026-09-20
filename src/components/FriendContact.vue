<template>
  <li>
    <h2>{{ name }} {{ friendIsFavorite === '1' ? '(Favorite)' : '' }}</h2>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phone }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ email }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true
    },
    phone: {
      type: String,
      required: true
    },
    email: {
      type: String,
      required: true
    },
    isFavorite: {
      type: String,
      required: false,
      default: '0',
      validator: function (value) {
        return value === '1' || value === '0'
      }
    }
  },
  data() {
    return {
      detailsAreVisible: false,
      friendIsFavorite: this.isFavorite
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      if(this.friendIsFavorite === '1') {
        this.friendIsFavorite = '0'
      } else {
        this.friendIsFavorite = '1'
      }
    }
  }
};
</script>