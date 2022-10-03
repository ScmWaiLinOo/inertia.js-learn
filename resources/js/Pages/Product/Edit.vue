<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-6">
        <div class="card">
          <div class="card-header">Edit A Product</div>
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
  methods: {
    submit(form) {
      this.$inertia.put(`/product/${this.product.id}`, form);
    },
  },
};
</script>

<style>
</style>