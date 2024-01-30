<script setup>
import Nav from "./components/Nav.vue";
import Form from "./components/RegisterForm.vue";
components: { Nav, Form }
</script>

<template>
  <div id="app">
    <header>
      <Nav></Nav>
    </header>
    <main>
      <Form></Form>
    </main>
  </div>
</template>