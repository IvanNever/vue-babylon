<template>
  <Scene>
    <Camera type="arcRotate" :radius="7.5"></Camera>
    <HemisphericLight
      v-if="light === 'hemispheric'"
      :diffuse="mainColor"
    ></HemisphericLight>
    <DirectionalLight v-else-if="light === 'directional'"></DirectionalLight>
    <PointLight v-else-if="light === 'point'"></PointLight>
    <SpotLight v-else-if="light === 'spot'"></SpotLight>
    <Entity>
      <template v-if="animate">
        <Animation property="rotation.y" :duration="5">
          <Key frame="0%" :value="0"></Key>
          <Key frame="25%" :value="0.5"></Key>
          <Key frame="75%" :value="-0.5"></Key>
          <Key frame="100%" :value="0"></Key>
        </Animation>
        <Animation property="rotation.x" :duration="5">
          <Key frame="0%" :value="0"></Key>
          <Key frame="10%" :value="0.5"></Key>
          <Key frame="20%" :value="0"></Key>
          <Key frame="30%" :value="0.5"></Key>
          <Key frame="40%" :value="0"></Key>
          <Key frame="50%" :value="0.5"></Key>
          <Key frame="60%" :value="0"></Key>
          <Key frame="70%" :value="0.5"></Key>
          <Key frame="80%" :value="0"></Key>
          <Key frame="90%" :value="0.5"></Key>
          <Key frame="100%" :value="0"></Key>
        </Animation>
      </template>
      <Asset
        src="https://www.babylonjs-playground.com/scenes/skull.babylon"
        :scaling="[0.05, 0.05, 0.05]"
      >
      </Asset>
    </Entity>
  </Scene>
</template>

<script>
export default {
  name: "Skull",
  props: ["animate", "light", "mainColor"],
};
</script>

<style scoped></style>
