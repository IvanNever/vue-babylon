<template>
  <Scene>
    <Camera type="arcRotate" :radius="7.5"></Camera>
    <Entity>
      <Animation
        property="rotation.y"
        :duration="5"
        :end="Math.PI * 2"
        v-if="animate"
      ></Animation>
      <DirectionalLight
        v-if="light === 'directional'"
        specular="#0F0"
        :diffuse="mainColor"
        :direction="[0, 0, 100]"
      ></DirectionalLight>
      <HemisphericLight v-else-if="light === 'hemispheric'"></HemisphericLight>
      <PointLight v-else-if="light === 'point'"></PointLight>
      <SpotLight v-else-if="light === 'spot'"></SpotLight>
    </Entity>
    <IcoSphere>
      <Material diffuse="#FF0"></Material>
      <template v-if="animate">
        <Animation
          property="rotation.x"
          :duration="3"
          :end="Math.PI * 2"
        ></Animation>
        <Animation
          property="rotation.y"
          :duration="3"
          :end="Math.PI * 2"
        ></Animation>
      </template>
    </IcoSphere>
  </Scene>
</template>

<script>
export default {
  name: "Sphere",
  props: ["animate", "light", "mainColor"],
};
</script>

<style scoped></style>
