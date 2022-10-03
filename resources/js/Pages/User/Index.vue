<template>
  <div class="container">
    <div class="my-5 row justify-content-between">
      <div class="col">
        <inertia-link href="/user/create" class="btn btn-primary">
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
          <td>Email</td>
          <td>Date</td>
          <td>Actions</td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users.data" :key="user.id">
          <td>{{ user.id }}</td>
          <td>{{ user.name }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.created_at }}</td>
          <td>
            <inertia-link
              :href="`/user/${user.id}/edit`"
              class="btn btn-success"
            >
              Edit
            </inertia-link>
            <button @click="destroy(user.id)" class="btn btn-danger">
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    <pagination :links="users.links"></pagination>
  </div>
</template>

<script>
import Pagination from "../../components/Pagination";
export default {
  components: {
    Pagination,
  },
  props: ["users", "filter"],
  data() {
    return {
      search: this.filter,
    };
  },
  methods: {
    submit() {
      this.$inertia.get(`/user?search=${this.search}`);
    },
    destroy(id) {
      if (confirm("Are you sure to delete?")) {
        this.$inertia.delete(`/user/${id}`);
      }
    },
  },
};
</script>

<style>
</style>