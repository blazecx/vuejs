<script>
export default {
  data(){
    return{
      currentIndex:0,
      items:[
        {
          img:'https://i.pinimg.com/564x/44/31/90/4431905d06e9e17cad6447c32acefb4b.jpg'
        },
        {
          img:'https://i.pinimg.com/236x/0e/bd/26/0ebd262c4b7f69f7ec915dbd8509328f.jpg'
        },
        {
          img:'https://i.pinimg.com/236x/1b/9b/34/1b9b3430f3e89b95c22937d7c353737e.jpg'
        }
      ]
    }
  },
  methods:{
    next(){
      this.currentIndex = (this.currentIndex + 1) % this.items.length;
    },
    prev(){
      this.currentIndex = (this.currentIndex - 1 + this.items.length) % this.items.length;
    }
  }
}
</script>

<template>
  <div class="carousel">
    <div class="carousel-inner" :style="{transform:`translateX(-${currentIndex * 100}%)`}">
     <div v-for="(item,index) in items" :key="index"  class="carousel-item">

       <img :src="item.img" alt="">
     </div>*

    </div>

    <button @click="prev">Prev</button>
    <button @click="next">Next</button>
  </div>
</template>

<style scoped>
.carousel {
  position: relative;
  width:800px;
  overflow: hidden;
}

.carousel-inner {
  display: flex;
  justify-content: space-between;
  transition: transform 0.5s ease;

}

.carousel-item {
  flex: 0 0 100%;
  padding: 1rem;
  box-sizing: border-box;
  object-fit: contain;
  width: 100%;
  height: 100%;

}
</style>