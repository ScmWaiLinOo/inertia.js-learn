<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-6">
        <div class="card">
          <div class="card-header">Edit A User</div>
          <div class="card-body">
            <user-form
              :user="user"
              :errors="errors"
              @submit="submit"
            ></user-form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import UserForm from "./_Form";
export default {
  components: {
    UserForm,
  },
  props: ["user", "errors"],
  methods: {
    submit(form) {
      this.$inertia.put(`/user/${this.user.id}`, form);
    },
  },
};
</script>

<style>
</style>