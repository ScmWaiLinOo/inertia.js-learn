<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-6">
        <div class="card">
          <div class="card-header">Create A Product</div>
          <div class="card-body">
            <product-form
              :product="product"
              :errors="errors"
              @submit="submit"
            ></product-form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ProductForm from "./_Form";
export default {
  components: {
    ProductForm,
  },
  props: ["product", "errors"],
  data() {
    return {
      form: {
        name: null,
        price: null,
        image: null,
      },
    };
  },
  methods: {
    submit(form) {
      this.$inertia.post("/product", form);
    },
  },
};
</script>

<style>
</style>