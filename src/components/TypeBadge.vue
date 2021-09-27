<template>
  <p :class="`type ${type}`">{{type.trim()}}</p>
</template>
<script>
export default {
  name: "TypeBadge",
  props: ["type"],
}
</script>
<style scoped>
.type { 
    margin: 1px;
    padding: 1px 15px;
    display: inline;
    border-radius: 8px;
    color:white;
    text-transform: capitalize;
}
.grass {
    background-color:yellowgreen;
}
.poison {
    background-color:mediumpurple;
}
.fire {
    background-color: orange;
}
.water {
    background-color: cornflowerblue;
}
.fairy {
    background-color: lightpink;
}
.bug {
    background-color:mediumseagreen;
}
.normal {
    background-color: lightgray;
}
.electric {
    background-color: gold;
}
.fighting {
    background-color: brown;
}
.psychic {
    background-color:hotpink; 
}
.rock {
    background-color:olive;
}
.steel {
    background-color:cadetblue;
}
.ice {
    background-color:paleturquoise;
}
.ghost {
    background-color:rebeccapurple;
}
.dragon {
    background-color:navy;
}
.fighting {
    background-color:firebrick;
}
.ground {
    background-color:peru;
}
.flying {
    background-color:lightblue;
}
</style>