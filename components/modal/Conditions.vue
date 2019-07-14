<template>
  <div :class="[ openModal ? 'is-active' : '', 'modal' ]">
    <div class="modal-background"></div>
    <div class="modal-card">
      <header class="modal-card-head">
        <p class="modal-card-title">{{ modalTitle }}</p>
        <button class="delete" aria-label="close" @click="closeModal(false)"></button>
      </header>
      <section class="modal-card-body">
        <div v-if="!isConditionsSection">
         
          <div v-if="products.length === 0">
            <p>{{ cartEmptyLabel }}</p>
          </div>
        </div>
        <div v-if="isConditionsSection">
          <form
            id="payform"
            onsubmit="return false;"
            method="POST"
            action="https://voguepay.com/pay/"
          >
            <input type="hidden" name="v_merchant_id" value="qa331322179752" />
            <input type="hidden" name="merchant_ref" value="234-567-890" />
            <input type="hidden" name="memo" value="Bulk order from McAckney Web Shop" />

            <input type="hidden" name="item_1" value="Face Cap" />
            <input type="hidden" name="description_1" value="Blue Zizi facecap" />
            <input type="hidden" name="price_1" value="2000" />

            <input type="hidden" name="item_2" value="Laban T-shirt" />
            <input type="hidden" name="description_2" value="Green XXL" />
            <input type="hidden" name="price_2" value="3000" />

            <input type="hidden" name="item_3" value="Black Noni Shoe" />
            <input type="hidden" name="description_3" value="Size 42" />
            <input type="hidden" name="price_3" value="8000" />

            <input type="hidden" name="developer_code" value="pq7778ehh9YbZ" />
            <input type="hidden" name="store_id" value="25" />

            <input type="hidden" name="total" value="13000" />

            <input type="hidden" name="name" value="Customer name" />
            <input type="hidden" name="address" value="Customer Address" />
            <input type="hidden" name="city" value="Customer City" />
            <input type="hidden" name="state" value="Customer State" />
            <input type="hidden" name="zipcode" value="Customer Zip/Post Code" />
            <input type="hidden" name="email" value="Customer email" />
            <input type="hidden" name="phone" value="Customer phone " />
            <input
              type="image"
              src="http://voguepay.com/images/buttons/buynow_blue.png"
              alt="Submit"
            />
          </form>
        </div>
      </section>
      <footer class="modal-card-foot">
        <button
          v-show="products.length > 0 && !isConditionsSection"
          class="button is-success"
          @click="onNextBtn"
        >{{ buyLabel }}</button>
        <button
          v-if="isConditionsSection"
          class="button is-success"
          @click="closeModal(true)"
        >{{ closeLabel }}</button>
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  name: "Conditions",
  data() {
    return {
      modalTitle: "Conditions",
      removeLabel: "Remove from cart",
      cartEmptyLabel: "Your cart is empty",
      closeLabel: "Close",
      isConditionsSection: false
    };
  },

  computed: {
    products() {
      return this.$store.getters.productsAdded;
    },
    openModal() {
      if (this.$store.getters.isConditionsModalOpen) {
        return true;
      } else {
        return false;
      }
    },
    buyLabel() {
      let totalProducts = this.products.length,
        productsAdded = this.$store.getters.productsAdded,
        pricesArray = [],
        productLabel = "",
        finalPrice = "",
        quantity = 1;

      productsAdded.forEach(product => {
        if (product.quantity >= 1) {
          quantity = product.quantity;
        }

        pricesArray.push(product.price * quantity); // get the price of every product added and multiply quantity
      });

      finalPrice = pricesArray.reduce((a, b) => a + b, 0); // sum the prices

      if (totalProducts > 1) {
        // set plural or singular
        productLabel = "products";
      } else {
        productLabel = "product";
      }
      return `Buy ${totalProducts} ${productLabel} at £${finalPrice}`;
    },
    isUserLoggedIn() {
      return this.$store.getters.isUserLoggedIn;
    }
  },

  methods: {
    closeModal(reloadPage) {
      this.$store.commit("showConditionsModal", false);

      if (reloadPage) {
        window.location.reload();
      }
    },
    removeFromCart(id) {
      let data = {
        id: id,
        status: false
      };
      this.$store.commit("removeFromCart", id);
      this.$store.commit("setAddedBtn", data);
    },
    onNextBtn() {
      this.isConditionsSection = true;
    },

    onPrevBtn() {
      this.isConditionsSection = false;
    }
  }
};
</script>

