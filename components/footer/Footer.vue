<template>
  <div class="footer">
    <div class="columns container">
      <div class="column has-text-justify">
        <a href="#">
          <p>With ❤ From Arts Love World | &trade;</p>
        </a>
      </div>

      <div class="column has-text-center">
        <a href="#">
          <p>&copy; Copyright 2019, All Rights Reserve.</p>
        </a>
      </div>

      <div class="column has-text-justify">
        <p>
          <nuxt-link :to="{ name: 'Terms' }">
            <h3>Terms And Conditions</h3>
          </nuxt-link>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "VmFooter",
  methods: {
    showCheckoutModal() {
      this.$store.commit("showCheckoutModal", true);
    }
  }
};
</script>

<style lang="scss" scoped>
.footer {
  background: #b9e2fc;
  color: black;
}
</style>
