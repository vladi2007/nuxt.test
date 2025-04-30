<script>

const response = await fetch('https://jsonplaceholder.typicode.com/users');
const users = await response.json();
console.log(users)
export default{
    name: 'Contacts',
    data() {
        return {
            items: users
            
        }
    }
}
</script>

<template>
  <div>
    <div v-for="item in items" :key="item.id">
       <div class="row"> <p>{{ item.name  }}</p> <p>{{ item.username }}</p> <p>{{ item.email }}</p></div>
    </div>
    
  </div>
</template>

<style>
.row {display: inline-flex;} 
.row > p {margin-left: 20px;}
</style>
