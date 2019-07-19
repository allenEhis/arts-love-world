<template>
  <div>
    <nav class="navbar" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <nuxt-link :to="{ name: 'index' }" class="navbar-item">
          <h1 class="title is-3 is-flex-mobile"></h1>
        </nuxt-link>

        <a
          role="button"
          class="navbar-burger burger"
          @click="isMenuOpen = !isMenuOpen"
          aria-label="menu"
          aria-expanded="false"
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div class="navbar-menu">
        <div class="navbar-start">
          <div class="navbar-item field">
            <VmSearch></VmSearch>
          </div>
        </div>

        <div class="navbar-menu">
          <nuxt-link :to="{ name: 'index' }" class="navbar-item">
            <h1>
              <span class="icon">
                <i class="fa fa-home"></i>
              </span> Home
            </h1>
          </nuxt-link>
        </div>

        <div class="navbar-menu">
          <nuxt-link :to="{ name: 'policy' }" class="navbar-item">
            <h1>
              <span class="icon">
                <i class="fa fa-credit-card"></i>
              </span> Sales Policy
            </h1>
          </nuxt-link>
        </div>

        <div class="navbar-menu">
          <nuxt-link :to="{ name: 'mailorder' }" class="navbar-item">
            <h1>
              <span class="icon">
                <i class="fa fa-envelope"></i>
              </span> Mail Order
            </h1>
          </nuxt-link>
        </div>

        <div class="navbar-menu">
          <nuxt-link :to="{ name: 'contact' }" class="navbar-item">
            <h1>
              <span class="icon">
                <i class="fa fa-inbox"></i>
              </span> Contact Us
            </h1>
          </nuxt-link>
        </div>

        <div class="navbar-end">
          <div class="navbar-item shopping-cart" @click="showCheckoutModal">
            <span class="icon">
              <i class="fa fa-shopping-cart"></i>
            </span>
            <span :class="[numProductsAdded > 0 ? 'tag is-info' : '']">{{ numProductsAdded }}</span>
          </div>
        </div>
      </div>

      <!-- For mobile and tablet -->
      <div v-show="isMenuOpen" class="navbar-end">
        <VmMenu></VmMenu>
      </div>

      <!-- For desktop -->
      <div class="navbar-end is-hidden-mobile">
        <VmMenu></VmMenu>
      </div>
    </nav>
  </div>
</template>

<script>
import VmMenu from "../menu/Menu";
import VmSearch from "../search/Search";

export default {
  name: "VmHeader",

  data() {
    return {
      linkedinTooltip: "Follow us on Linkedin",
      facebookTooltip: "Follow us on Facebook",
      twitterTooltip: "Follow us on Twitter",
      instagramTooltip: "Follow us on Instagram",
      isCheckoutActive: false,
      isMenuOpen: false
    };
  },

  components: {
    VmSearch,
    VmMenu
  },

  computed: {
    numProductsAdded() {
      return this.$store.getters.productsAdded.length;
    }
  },

  methods: {
    showCheckoutModal() {
      this.$store.commit("showCheckoutModal", true);
    }
  }
};
</script>

<style lang="scss" scoped>
.title {
  background: url("../../static/vuemmerce-logo.png") no-repeat;
  background-position: 50% 50%;
  background-size: 240px;
  width: 250px;
  height: 40px;
  border-radius: 30%;
}
.shopping-cart {
  cursor: pointer;
}
a {
  color: grey;
}
</style>
