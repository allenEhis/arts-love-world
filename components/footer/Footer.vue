<template>
  <div class="footer">
    <div class="columns container center">
      <div class="column has-text-justify">
        <h6 class="title">Address</h6>
        <p>
          <span class="icon">
            <i class="fa fa-map-marker"></i>
          </span>30, Afolabi Aina Street,
          <br />Ikeja, Lagos State, Nigeria.
        </p>
        <br />
        <a href="#">
          <p>With ❤ From Arts Love World | &trade;</p>
        </a>
        <br />
        <a href="#">
          <p>&copy; Copyright 2019, All Rights Reserve.</p>
        </a>
      </div>

      <div class="column has-text-center">
        <div>
          <h6 class="title">24/7 Support</h6>
          <nuxt-link :to="{ name: 'contact' }">
            <h3 class="subtitle">
              <span class="icon">
                <i class="fa fa-envelope-o"></i>
              </span> support@artsloveworld.store
            </h3>
          </nuxt-link>
        </div>
        <br />
        <div>
          <p>
            <span class="icon">
              <i class="fa fa-phone"></i>
            </span> +2349017318250
          </p>
        </div>
      </div>

      <div class="column has-text-justify">
        <h6 class="title">Links</h6>
        <p>
          <nuxt-link :to="{ name: 'index' }">
            <h3>
              <span class="icon">
                <i class="fa fa-home"></i>
              </span>Home
            </h3>
          </nuxt-link>
        </p>
        <br />
        <p>
          <nuxt-link :to="{ name: 'policy' }">
            <h3>
              <span class="icon">
                <i class="fa fa-credit-card"></i>
              </span>Sales Policy
            </h3>
          </nuxt-link>
        </p>
        <br />
        <p>
          <nuxt-link :to="{ name: 'mailorder' }">
            <h3>
              <span class="icon">
                <i class="fa fa-envelope"></i>
              </span>Mail Order
            </h3>
          </nuxt-link>
        </p>
        <br />
        <p>
          <nuxt-link :to="{ name: 'contact' }">
            <h3>
              <span class="icon">
                <i class="fa fa-inbox"></i>
              </span>Contact Us
            </h3>
          </nuxt-link>
        </p>
        <br />
        <p>
          <nuxt-link :to="{ name: 'Terms' }">
            <h3>
              <span class="icon">
                <i class="fa fa-file-pdf-o"></i>
              </span>Terms And Conditions
            </h3>
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
