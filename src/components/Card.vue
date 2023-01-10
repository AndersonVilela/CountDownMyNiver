<template>
  <div class="ContainerCard">
    <span class="number">{{ number }}</span>
    <span class="description">{{ description }}</span>
  </div>
</template>

<script lang="ts">
export default {
  props: ["number", "description"],
    
};

</script>

<style>
.ContainerCard {
  margin-top: 43px;
  width: 199px;
  height: 199px;
  left: 281px;
  top: 516px;

  background: #080f1a;
  border-radius: 22px;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.number {
  font-weight: 900;
  font-size: 64px;
  line-height: 96px;
  text-align: center;

  color: #ffffff;
}
.description {
  font-style: normal;
  font-weight: 300;
  font-size: 16px;
  line-height: 24px;
  text-align: center;

  color: #a5deff;
}
</style>
