<template>
  <article class="card">
    <div class="img-wrapper">
      <img :src="property.img" :alt="property.title" />

      <span v-if="!property.available" class="badge">
        Not Available
      </span>
    </div>

    <h3>{{ property.title }}</h3>
    <p>{{ property.location }}</p>
    <p class="price">R{{ property.price }}</p>

    <div class="footer">
      <small>{{ property.type }}</small>

      <button class="fav" @click="$emit('toggle-fav', property.id)">
        {{ property.favourite ? "★" : "☆" }}
      </button>
    </div>
  </article>
</template>

<script>
export default {
  props: ["property"]
};
</script>

<style scoped>
.card {
  background: #133c55;
  color: #fff;
  padding: 14px;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
}
.card:hover{
  transform:translateY(-5px);
  box-shadow: 0 2px 8px rgba(13, 33, 161);
}
.img-wrapper {
  position: relative;
}

img {
  width: 100%;
  border-radius: 8px;
}

.badge {
  position: absolute;
  top: 8px;
  left: 8px;
  background: #d0021b;
  color: white;
  padding: 4px 8px;
  font-size: 12px;
  border-radius: 4px;
}

.price {
  font-weight: bold;
  margin: 6px 0;
}

.footer {
  margin-top: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.fav {
  color: #fff;
  background: none;
  border: none;
  font-size: 20px;
  cursor: pointer;
}
</style>
