<template>
  <section class="dropdown">
   <div class="selected-item">
    
  
 </div>
   
   
   
    <input 
    type="search" 
    v-model="search" 
    class="search" 
    placeholder=" найти.. "
    />
    <p>{{search}}</p>
    
  


    <div class="options"> 
      
     
      
      <Modal @click="toggleModal" :modalActive="modalActive">
        <div class="modal-content">
          <h1> <ul>
            <li v-for="item in searchHandler" :key="item.name">
              <p><span> Имя: {{item.name}}</span></p>
              <p><span> Фамилия: {{item.surname}}</span></p>
              <p><span> Баркод: {{item.barkod}}</span></p>
              <p><span> Возраст: {{item.age}}</span></p>
              <p><span> Gpa: {{item.gpa}}</span></p>
              <p><span> Пол: {{item.gender}}</span></p>
              <p><span> Курс: {{item.course}}</span></p>
            </li>
            
          </ul></h1>
          
        </div>
      </Modal>
      <button @click="toggleModal" type="button">Найти информацию о студенте</button>
      
    </div>
    
    
    </section>
 
</template>

<script>
import Modal from '@/components/HelloWorld.vue';
import { students } from './data';
import {ref} from 'vue';




export default {
  name: "App",
  components: {
    Modal,
  },
  setup(){
    const modalActive = ref(false);
    const toggleModal = () => {
      modalActive.value = !modalActive.value;
    }

    return {modalActive, toggleModal};
  },
 
 

data(){
  return {
    search: '',
    data: []
  

  }
  
},



created() {
this.data = students;
console.log(this.data);
},
computed: {
  searchHandler() {
    return this.data.filter(elem => {
      return elem.name.includes(this.search);
    })
  }
}
 
}
</script>



<style lang="scss">
.dropdown {
  max-width: 350px;
  position: relative;
  margin: 0 auto;
  padding:10px;
}
.selected-item{
  height: 40px;
 
 
  padding:2px 10px;
  display: flex;
  justify-content: space-between;
  align-items: center ;
  font-size: 20px;
  font-weight: 300;
  color: black;
}
.search {
  height: 80px;
  width: 350px;
  border: 2px solid chocolate;
  top: 46px;
  left: 0;
  right: 0;
  background-color:beige; 
  font-size: 30px;
}
.btn {
  
  background-color: chocolate;
  border: 2px solid chocolate;
  height: 40px;
  width: 100px;
  font-size: 20px;
  font-weight: 700;
  
}






#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  background-color:beige;
  height: 1000px;

  width: 1890px;
  display: flex;
  justify-content: center;
  align-items: center;

  .modal-content {
    display: flex;
    flex-direction: center;
    text-align: center;
    
    h1, p {
      margin-bottom: 16px;
      flex-direction: column;
      text-align: center;

    }

    h1 {
      font-size: 32px;
      flex-direction: column;
      text-align: center;

    }
    p {
      font-size: 18px;
      flex-direction: column;
      text-align: center;

    }
  }
}

button {
  padding: 20px 30px;
  border: none;
  font-size: 16px;
  background-color:chocolate;
  color: beige;
  cursor: pointer;
  text-align: center;


}

.span {
  margin-bottom: 16px;
  justify-content: center;
  align-items: center;
  text-align: center;
  
}
</style>
