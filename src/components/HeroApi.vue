<template>
  <div>
  <nav class="navbar bg-dark">
      <div class="container">
        <a class="navbar-brand" href="#">
          
        </a>
      </div>
    </nav>
    <header>
      <div class="d-flex justify-content-evenly p-3">
    
      </div>
    </header>
  
      <form @submit.prevent="setHeroes">
        <div class="container ps-5 ms-5">
          <div class="container mx-5" style="width: 800px">
            <div class="container mx-5">
              <h1>Encuentra tu SuperHero</h1>
              <p>Ingresa el número del SuperHero a buscar</p>
            </div>

            <div class="mb-3 ps-2 mx-5" style="width: 120%">
              <input v-model="input"
                id="heroInput"
                type="number"
                class="form-control"
                width="40"
                min="1"
                max="732"
                step="1"
              />
            </div>
            <div class="mx-5 ps-2">
              <button type="submit" class="btn btn-primary">Buscar</button>
            </div>
          </div>
        </div>
      </form>
  
   
   <div>
    <p v-for="(heroe, index) in heroes" :key="index">{{ heroe.name }}</p>
     
    </div>
   
 </div>
 
 
</template>

<script>
import axios from "axios";

export default {
 name: "HeroApi",
 data() {
   return {
     heroes: [],
     input: "",
   };
 },
 methods: {
   async getHeroes() {
     try {
       const url = "https://superheroapi.com/api.php/3033707663582647/" + this.input;

       const { data } = await axios.get(url);
       return data;
       // const response = await axios.get(url);
       // return response.data;
       /* Con destructuring */
     } catch (error) {
       console.log(error);
     }
   },

   async setHeroes() {
     const heroesResponse = await this.getHeroes();
     console.log(heroesResponse);
     this.heroes.push(heroesResponse);
   },
 },
};
</script>

<style>

</style>
