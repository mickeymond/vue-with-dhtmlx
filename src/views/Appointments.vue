<script lang="ts">

import {List as ListDHX} from "dhx-suite";
import {faker} from '@faker-js/faker';
import {RouterLink} from "vue-router";

export default {
  name: "Appointments",
  components: {RouterLink},
  data: () => ({
    list: null,
  }),
  mounted() {
    this.list = new ListDHX(this.$refs.list, {
      css: "dhx_widget--bordered dhx_widget--bg_white",
      template: item => `<div class="card">
  <div class="card-content">
    <div class="media">
      <div class="media-left">
        <figure class="image is-48x48">
          <img src="${faker.image.avatar()}" alt="Placeholder image">
        </figure>
      </div>
      <div class="media-content">
        <p class="title is-4">${faker.person.fullName()}</p>
        <p class="subtitle is-6">${faker.internet.email()}</p>
      </div>
    </div>

    <div class="content">
      ${faker.person.jobDescriptor()}
      <br>
      <time datetime="2016-1-1">11:09 PM - 1 Jan 2016</time>
    </div>
  </div>
</div><br/>`,
      height: 400,
    });

    this.list.data.load("https://jsonplaceholder.typicode.com/users");
  },
  beforeUnmount() {
    if (this.list) {
      this.list.destructor();
    }
  },
}
</script>

<template>
  <section class="container section is-max-desktop">
    <p class="title">All Appointments</p>
    <!-- Main container -->
    <nav class="level">
      <!-- Left side -->
      <div class="level-left"></div>
      <!-- Right side -->
      <div class="level-right">
        <RouterLink to="/add">
          <button class="button is-primary level-item">Add Appointment</button>
        </RouterLink>
      </div>
    </nav>
    <div ref="list"></div>
  </section>
</template>
