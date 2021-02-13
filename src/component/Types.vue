<template>
    <div class="container-types">
          <div id="enlinea" v-for="tipo in tipos" :key="tipo.slot">
            <component-type :nombre="tipo.type.name"  >
            </component-type >
          </div>
    </div>

</template>
<script>
import componentType  from  './Type.vue'
export default {
    name:'componentTypes',
    components: {
      componentType
    },
    props: ['tipos']
  
}
</script>
<style >


#enlinea {
  display: inline-block;
  margin-inline: 5px;
}

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