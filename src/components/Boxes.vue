<template>
  <Scene>
    <Camera type="arcRotate" :radius="7.5"></Camera>
    <HemisphericLight
      v-if="light === 'hemispheric'"
      :diffuse="mainColor"
    ></HemisphericLight>
    <DirectionalLight
      v-else-if="light === 'directional'"
      :diffuse="mainColor"
    ></DirectionalLight>
    <PointLight v-else-if="light === 'point'" :diffuse="mainColor"></PointLight>
    <SpotLight v-else-if="light === 'spot'" :diffuse="mainColor"></SpotLight>
    <Entity :position="[0, 0, 5]" :scaling="[0.5, 0.5, 0.5]">
      <template v-if="animate">
        <Animation property="rotation.x" :duration="5">
          <Key frame="0%" :value="0"></Key>
          <Key frame="100%" :value="Math.PI * 2"></Key>
        </Animation>
        <Animation
          property="rotation.y"
          :duration="5"
          :end="Math.PI * 2"
        ></Animation>
        <Animation
          property="rotation.z"
          :duration="5"
          :end="Math.PI * 2"
        ></Animation>
      </template>
      <PointLight diffuse="#FF0000"></PointLight>
      <template v-for="x in [0, 4, -4]">
        <template v-for="y in [0, 4, -4]">
          <Box
            v-for="z in [0, 4, -4]"
            :position="[x, y, z]"
            :key="`${x},${y},${z}`"
          ></Box>
        </template>
      </template>
    </Entity>
  </Scene>
</template>

<script>
export default {
  name: "Boxes",
  props: ["animate", "light", "mainColor"],
};
</script>

<style scoped></style>
