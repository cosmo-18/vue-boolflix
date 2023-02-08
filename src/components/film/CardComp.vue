<template>
  <div class="card">
    <div class="thefront">
      <img
        class="poster"
        :src="`http://image.tmdb.org/t/p/w342/${singleItem.poster_path}`"
        alt="poster"
      />
    </div>
    <div class="theback">
      <!--title-->
      <div class="text-white content">
        <div class="fw-bold text-center">{{ singleItem.title }}</div>
      </div>
      <!--flag-->
      <div class="text-center">
        <img
          v-if="languages != 'EN'"
          :src="`https://www.countryflagicons.com/FLAT/32/${languages}.png`"
          alt="flag"
        />
        <img
          v-else
          src="https://www.countryflagicons.com/FLAT/32/US.png"
          alt="flag"
          class="mx-auto"
        />
      </div>

      <!--score-->
      <div class="d-flex text-white">
        <span class="fw-bold text-center fs-3 text-success mx-auto"
          >{{ singleItem.vote_average }}/10</span
        >
      </div>
      <!--score in stars image-->
      <div class="d-flex stars">
        <i
          class="fa-solid fa-star"
          v-for="index in this.stars"
          :key="index"
        ></i>
        <i
          class="fa-solid fa-star text-dark"
          v-for="index in 5 - this.stars"
          :key="index"
        ></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardComp",
  props: {
    singleItem: Object,
  },
  data() {
    return {
      stars: Math.ceil(this.singleItem.vote_average / 2),
      languages: this.singleItem.original_language.toUpperCase(),
    };
  },
};
</script>

<style scoped>
/***************
      CARD
****************/
.card {
  display: inline-block;
  width: 209px;
  height: 314px;
  transition: transform 1500ms;
  transform-style: preserve-3d;
  position: relative;
  border: none;
}

.card:hover {
  transform: rotateY(180deg);
}
.card > .thefront > img {
  max-width: 100%;
  display: inline-block;
}
.card:hover > .thefront > img {
  display: none;
}
/*******************
    THE FRONT
*********************/
.thefront {
  height: 314px;
}
.card:hover .thefront {
  display: none;
}
/*******************
      THE BACK
*********************/

.card:hover .theback {
  display: inline-block;
  background-color: rgb(137, 137, 137);

}
.theback {
  display: none;
  position: absolute;
  top: 0;
  left: 0;
  overflow-y: scroll;
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
  transform: rotateY(180deg);
  max-width: 209px;
  height: 314px;
  padding: 5px;
}

/* Hide scrollbar for Chrome, Safari and Opera */
.theback::-webkit-scrollbar {
  display: none;
}

/*******************
      STARS
*********************/

.flag {
  height: 54px;
  width: 70px;
}

/*******************
      STARS
*********************/

.stars {
  justify-content: center;
}
.stars * {
  color: gold;
}


.content{
  width: 200px;
}
</style>
Footer
