<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-6">
        <div class="card">
          <div class="card-header">Create A User</div>
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
  data() {
    return {
      form: {
        name: null,
        email: null,
        password: null,
      },
    };
  },
  methods: {
    submit(form) {
      this.$inertia.post("/user", form);
    },
  },
};
</script>

<style>
</style>