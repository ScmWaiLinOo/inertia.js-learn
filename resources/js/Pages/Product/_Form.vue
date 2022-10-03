<template>
  <form @submit.prevent="submit" method="post">
    <div class="form-group">
      <label>Name</label>
      <input
        type="text"
        v-model="form.name"
        class="form-control"
        :class="{ 'is-invalid': errors.name }"
      />
      <span v-if="errors.name" class="invalid-feedback">
        {{ errors.name[0] }}
      </span>
    </div>
    <div class="form-group">
      <label>Price</label>
      <input
        type="text"
        v-model="form.price"
        class="form-control"
        :class="{ 'is-invalid': errors.price }"
      />
      <span v-if="errors.price" class="invalid-feedback">
        {{ errors.price[0] }}
      </span>
    </div>
    <div class="form-group">
      <label>Image</label>
      <input
        type="text"
        v-model="form.image"
        class="form-control"
        :class="{ 'is-invalid': errors.image }"
      />
      <span v-if="errors.image" class="invalid-feedback">
        {{ errors.image[0] }}
      </span>
    </div>
    <button type="submit" class="btn btn-primary">Save</button>
    <inertia-link href="/product" class="btn btn-outline-secondary float-right">
      Cancel
    </inertia-link>
  </form>
</template>

<script>
export default {
  props: ["product", "errors"],
  data() {
    return {
      form: {
        name: this.product.name,
        price: this.product.price,
        image: this.product.image,
      },
    };
  },
  methods: {
    submit() {
      this.$emit("submit", this.form);
    },
  },
};
</script>

<style>
</style>