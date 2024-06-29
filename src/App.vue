<script setup>
import { items } from "./movies.json";
import { StarIcon } from "@heroicons/vue/24/solid";
</script>

<template>
  <div class="movies-container">
    <div v-for="item in items" :key="item.id" class="movie">
      <img :src="item.image" :alt="item.name" class="movie-image" />
      <h2>{{ item.name }}</h2>
      <p>{{ item.description }}</p>
      <div class="rating">
        <StarIcon
          v-for="star in 5"
          :key="star"
          class="star-icon"
          :class="{ active: star <= item.rating, inactive: star > item.rating }"
        />
      </div>
      <ul class="genres">
        <li v-for="genre in item.genres" :key="genre">{{ genre }}</li>
      </ul>
      <p v-if="item.inTheaters">In Theaters</p>
    </div>
  </div>
</template>

<style scoped>
.movies-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.movie {
  width: 300px;
  border: 1px solid #ccc;
  padding: 10px;
  border-radius: 5px;
}

.movie-image {
  width: 100%;
  height: auto;
  border-radius: 5px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.movie-image:hover {
  transform: scale(1.03);
}

.rating {
  display: flex;
  align-items: center;
  margin-top: 8px;
}

.star-icon {
  color: gold;
  width: 24px; /* Adjust the size of the star icon */
}

/* Additional styling for a nicer look */
.movie {
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: box-shadow 0.3s ease;
  overflow: hidden;
}

.movie:hover {
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

h2 {
  color: #333;
  font-size: 20px;
  margin-top: 10px;
}

p {
  color: #666;
  font-size: 14px;
  line-height: 1.6;
}

.genres li {
  background-color: #007bff;
  color: #fff;
  border-radius: 15px;
  padding: 5px 10px;
  margin: 5px 5px 5px 0;
  font-size: 12px;
}
.star-icon.inactive {
  color: #ccc;
}
</style>
