<script lang="ts">
export default {}
</script>

<template>
  <section class="container section is-max-desktop">
    <p class="title">Add An Appointment</p>
    <!-- Main container -->
    <nav class="level">
      <!-- Left side -->
      <div class="level-left"></div>
      <!-- Right side -->
      <div class="level-right">
        <RouterLink to="/">
          <button class="button is-primary level-item">Goto Appointments</button>
        </RouterLink>
      </div>
    </nav>
    <div ref="list"></div>
  </section>
</template>

<style>
</style>
