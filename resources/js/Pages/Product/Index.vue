<template>
  <div class="container">
    <div class="my-5 row justify-content-between">
      <div class="col">
        <inertia-link href="/product/create" class="btn btn-primary">
          Create
        </inertia-link>
      </div>

      <div class="col-4">
        <form @submit.prevent="submit">
          <div class="input-group">
            <input
              type="text"
              v-model="search"
              class="form-control"
              placeholder="Search..."
            />
            <div class="input-group-append">
              <button class="btn btn-outline-secondary" type="submit">
                Search
              </button>
            </div>
          </div>
        </form>
      </div>
    </div>
    <table class="table">
      <thead>
        <tr>
          <td>ID</td>
          <td>Name</td>
          <td>price</td>
          <td>Image</td>
          <td>Created_at</td>
          <td>Actions</td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products.data" :key="product.id">
          <td>{{ product.id }}</td>
          <td>{{ product.name }}</td>
          <td>{{ product.price }}</td>
          <td>{{ product.image }}</td>
          <td>{{ product.created_at }}</td>
          <td>
            <inertia-link
              :href="`/product/${product.id}/edit`"
              class="btn btn-success"
            >
              Edit
            </inertia-link>
            <button @click="destroy(product.id)" class="btn btn-danger">
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    <pagination :links="products.links"></pagination>
  </div>
</template>

<script>
import Pagination from "../../components/Pagination";
export default {
  components: {
    Pagination,
  },
  props: ["products", "filter"],
  data() {
    return {
      search: this.filter,
    };
  },
  methods: {
    submit() {
      this.$inertia.get(`/product?search=${this.search}`);
    },
    destroy(id) {
      if (confirm("Are you sure to delete?")) {
        this.$inertia.delete(`/product/${id}`);
      }
    },
  },
};
</script>

<style>
</style>