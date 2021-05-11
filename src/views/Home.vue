<template>
  <div class="container">
    <h1>Babylon Demo</h1>
    <div class="control-panel">
      <h2>Entity:</h2>
      <select v-model="entity" @change="changeEntity">
        <option value="skull">Skull</option>
        <option value="boxes">Boxes</option>
        <option value="sphere">IcoSphere</option>
      </select>
      <h2>Light:</h2>
      <select v-model="light">
        <option value="hemispheric">HemisphericLight</option>
        <option value="directional">DirectionalLight</option>
        <option value="point">PointLight</option>
        <option value="spot">SpotLight</option>
      </select>
      <h2>Main color</h2>
      <select v-model="mainColor">
        <option value="#FFF">White</option>
        <option value="#F00">Red</option>
        <option value="#008800">Green</option>
        <option value="#00F">Blue</option>
      </select>
      <h2>Animation:</h2>
      <button @click="onAnimate">Animate</button>
    </div>
    <Skull
      :animate="animate"
      :light="light"
      :mainColor="mainColor"
      v-if="entity === 'skull'"
      :key="animate"
    />
    <Boxes
      :animate="animate"
      :light="light"
      :mainColor="mainColor"
      v-else-if="entity === 'boxes'"
      :key="animate"
    />
    <Sphere
      :animate="animate"
      :light="light"
      :mainColor="mainColor"
      v-else-if="entity === 'sphere'"
      :key="animate"
    ></Sphere>
  </div>
</template>

<script>
import Skull from "@/components/Skull";
import Boxes from "@/components/Boxes";
import Sphere from "@/components/Sphere";

export default {
  components: {
    Skull,
    Boxes,
    Sphere,
  },
  name: "Home",
  data() {
    return {
      animate: false,
      entity: "skull",
      light: "hemispheric",
      mainColor: "#FFF",
    };
  },
  methods: {
    onAnimate() {
      this.animate = !this.animate;
    },
    changeEntity() {
      this.animate = false;
      if (this.entity === "skull" || this.entity === "boxes") {
        this.light = "hemispheric";
      } else {
        this.light = "directional";
      }
    },
  },
};
</script>

<style scoped>
h1 {
  position: fixed;
  top: 20px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 30px;
  text-align: center;
  text-transform: uppercase;
  color: #fff;
}
.control-panel {
  position: fixed;
  left: 0;
  top: 0;
  padding: 200px 50px;
  height: 100%;

  display: flex;
  flex-direction: column;
}
button {
  font-size: 20px;
  font-family: inherit;
  font-weight: bold;
  padding: 10px 40px;
  background-color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}
select {
  margin-bottom: 30px;
  font-size: 20px;
  font-family: inherit;
  font-weight: bold;
  padding: 10px 40px;
  background-color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  outline: none;
}
h2 {
  color: #fff;
  text-align: left;
}
</style>
