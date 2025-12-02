<script setup></script>

<template>
  <div>
  <NavBar :favourites="favouriteCount"/>

    <HeaderBar 
      :total="filteredProperties.length"
      v-model="searchQuery"
      :sortOrder="sortOrder"
      @toggle-sort="toggleSort"
    />

    <ListingsGrid
      :properties="filteredProperties"
      @toggle-fav="toggleFavourite"
    />
  </div>
</template>

<script>

import NavBar from "./components/NavBar.vue";
import HeaderBar from "./components/HeaderBar.vue";
import ListingsGrid from "./components/ListingsGrid.vue";




export default {
  components: { NavBar, HeaderBar, ListingsGrid },

  data() {
    return {
      favouriteCount: 3,
      searchQuery: "",
      sortOrder: "asc",
      properties: [
        {
          id: 1,
          title: "4 Bedroom House for Sale",
          location: "8 Farringdon Steps, St James, Cape Town",
          price: 14500000,
          type: "House",
          available: true,
          img: "src/assets/properties/img1.jpg",
          favourite: false,
        },
        {
          id: 2,
          title: "2 Bedroom Apartment for Sale",
          location: "Isidore Cohen Place, Camps Bay, Cape Town",
          price: 11950000,
          type: "Apartment",
          available: false,
          img: "src/assets/properties/img2.jpg",
          favourite: false,
        },
        {
          id: 3,
          title: "4 Bedroom House for Sale",
          location: "2 Camps Bay Drive, 98b Camps Bay Drive, Camps Bay, Cape Town",
          price: 25950000,
          type: "House",
          available: true,
          img: "src/assets/properties/img3.jpg",
          favourite: false,
        },
        {
          id: 4,
          title: "3 Bedroom House for Sale",
          location: "Contact agent for street address",
          price: 39950000,
          type: "House",
          available: true,
          img: "src/assets/properties/img4.jpg",
          favourite: false,
        },
        {
          id: 5,
          title: "5 Bedroom House for Sale ",
          location: "Contact agent for street address",
          price: 95000000,
          type: "House",
          available: true,
          img: "src/assets/properties/img5.jpg",
          favourite: false,
        },
        {
          id: 6,
          title: "6 Bedroom House for Sale",
          location: "Contact agent for street address",
          price: 20900000,
          type: "House",
          available: true,
          img: "src/assets/properties/img6.jpg",
          favourite: false,
        },
        {
          id: 7,
          title: "4 Bedroom House for Sale",
          location: "C 71 Geneva, 71 Geneva, Camps Bay, Cape Town",
          price: 27900000,
          type: "House",
          available: true,
          img: "src/assets/properties/img7.jpg",
          favourite: false,
        },
        {
          id: 8,
          title: "5 Bedroom House for Sale",
          location: "1315 Quebec Road, 15 Quebec Road, Camps Bay, Cape Town",
          price: 89500000,
          type: "House",
          available: true,
          img: "src/assets/properties/img8.jpg",
          favourite: false,
        },
        {
          id: 9,
          title: "7 Bedroom House for Sale ",
          location: "Contact agent for street address",
          price: 35000000,
          type: "House",
          available: true,
          img: "src/assets/properties/img9.jpg",
          favourite: false,
        },
      ],
    };
  },

  computed: {
    filteredProperties() {
      let results = this.properties.filter((p) =>
        (p.title + p.location)
          .toLowerCase()
          .includes(this.searchQuery.toLowerCase())
      );

      if (this.sortOrder === "asc") {
        results.sort((a, b) => a.price - b.price);
      } else {
        results.sort((a, b) => b.price - a.price);
      }

      return results;
    },
  },

  methods: {
    toggleSort() {
      this.sortOrder = this.sortOrder === "asc" ? "desc" : "asc";
    },

    toggleFavourite(id) {
      const property = this.properties.find((p) => p.id === id);
      property.favourite = !property.favourite;
    },
  },
};
</script>

