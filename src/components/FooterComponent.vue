<template>
  <footer>
    <p>Copyright&copy; 2022.<span>Bramsurya Johannes Paulus</span></p>
  </footer>
</template>

<script>
export default {
  name: "FooterComponent",
};
</script>

<style lang="scss" scoped>
footer {
  text-align: center;
  background-color: #77a4e5;
  color: #fff;
  padding: 20px;
  bottom: 0;
  width: 100%;

  p {
    font-size: 14px;
    font-weight: 500;
  }

  span {
    font-weight: 700;
  }
}
</style>