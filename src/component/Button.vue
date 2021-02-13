<template>
   
        <button class="btn"  v-on:click="callback($event)" >
         <slot></slot>
    </button>
   
</template>
<script>
export default {
    name: 'componentButton',
    methods: {

      callback(e){
        this.$emit('click' , e);
      }
    }
}
</script>
<style >

/* Botones  */
.btn {
  background-color: whitesmoke;
  transition-duration: 0.4s;
  color: black;
  padding: 12px 32px;
  margin: 4px 4px;
  font-size: 16px;
  border: black solid 1px;
  outline-color: white;
  cursor: pointer;
  border-radius: 9999px;
  outline: none;
}

.btn:hover {
  background-color: gainsboro;
  transition-duration: 0.4s;
  color: black;
}

/* 
.btn:focus {
  background-color: rgba(0, 0, 255, 0.2);

} */

.green {
  background-color: green;
  color: white;
  border: green solid 1px;
  outline-color: white;
  outline: none;
}

.green:hover {
  background-color: white;
  transition-duration: 0.4s;
  color: green;
  outline: none;
}

.red {
  background-color: red;
  color: white;
  border: red solid 1px;
  outline-color: white;
  outline: none;
}

.red:hover {
  background-color: white;
  transition-duration: 0.4s;
  color: red;
}

.blue {
  background-color: blue;
  color: white;
  border: blue solid 1px;
  outline-color: white;
  outline: none;
}

.blue:focus {
  background-color: rgba(0, 0, 255, 0.6);
}

.blue:hover {
  background-color: white;
  transition-duration: 0.4s;
  color: blue;
}



</style>