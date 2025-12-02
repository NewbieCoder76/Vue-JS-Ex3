<template>
  <div class="grid">
    <PropertyCard 
      v-for="p in properties" 
      :key="p.id"
      :property="p"
      @toggle-fav="$emit('toggle-fav', p.id)"
    />
  </div>
</template>

<script>
import PropertyCard from "./PropertyCard.vue";

export default {
  props: ["properties"],
  components: { PropertyCard }
};
</script>
