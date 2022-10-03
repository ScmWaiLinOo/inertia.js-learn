<template>
  <nav>
    <ul class="pagination">
      <template v-for="(link, index) in links">
        <li
          :key="index"
          class="page-item"
          :class="[
            link.active ? 'active' : '',
            link.url === null ? 'disabled' : '',
          ]"
        >
          <div
            v-if="link.url === null"
            class="page-link"
            v-html="link.label"
          ></div>
          <inertia-link
            v-else
            :key="index"
            class="page-link"
            :href="link.url"
            v-html="link.label"
          ></inertia-link>
        </li>
      </template>
    </ul>
  </nav>
</template>

<script>
export default {
  props: {
    links: Array,
  },
};
</script>
