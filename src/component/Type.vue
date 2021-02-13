<template>
  <div>
    <div class="type-color" :class="nombre" >
      {{ nombre }}
    </div>
  </div>
</template>
<script>
export default {
  name: 'componentType',
  props: ['nombre']

};
</script>
<style >
.type-color {
  color: white;
  padding: 3px 15px;
  margin: 2px 2px;
  background-color: violet;
  border-radius: 5%;
  font-size: 16px;
}

/* fondo del tipo de pokemon */
.rock {
  background-color: red;
}
.poison {
  background-color: #a040a0;
}

.grass {
  background-color: #78c850;
}

.flying {
  background-color: cadetblue;
}

.psychic {
  background-color: deeppink;
}

.fire {
  background-color: #f08030;
}

.ghost {
  background-color: #705898;
}

.fighting {
  background-color: #c03028;
}
</style>