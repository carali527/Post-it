<template>
  <ul>
    <li>
      <p>{{ item.title }}</p>
      <p>{{ item.content }}</p>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["item"]
};
</script>