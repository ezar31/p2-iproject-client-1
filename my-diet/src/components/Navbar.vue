<script>
import { mapActions, mapWritableState } from "pinia";
import { useMainStore } from "../stores/main";
export default {
  computed: {
    ...mapWritableState(useMainStore, ["pageTitle"]),
  },
  methods: {
    ...mapActions(useMainStore, ["logout"]),
  },
};
</script>

<template>
  <nav class="navbar navbar-dark fixed-top navbar-expand-lg bg-dark px-5">
    <div class="container-fluid">
      <a class="me-4" href="#"
        ><img
          src="../assets/My_diet_logo.png"
          alt="My-diet_logo"
          style="height: 50px"
      /></a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNavDropdown"
        aria-controls="navbarNavDropdown"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div
        class="collapse navbar-collapse"
        style="display: flex; justify-content: space-between"
        id="navbarNavDropdown"
      >
        <ul class="navbar-nav">
          <li class="nav-item col">
            <router-link
              to="/"
              @click="pageTitle = 'Home'"
              class="nav-link active"
              aria-current="page"
              >Home</router-link
            >
          </li>

          <li class="nav-item dropdown">
            <a
              class="nav-link active dropdown-toggle"
              href="#"
              role="button"
              data-bs-toggle="dropdown"
              aria-expanded="false"
            >
              Calculator
            </a>
            <ul class="dropdown-menu">
              <li>
                <router-link
                  :to="{
                    name: 'calculator',
                    params: { feature: 'bmr' },
                  }"
                  @click="pageTitle = 'Basal Metabolic Rate'"
                  class="dropdown-item"
                  >BMR</router-link
                >
              </li>
              <li>
                <router-link
                  :to="{
                    name: 'calculator',
                    params: { feature: 'bmi' },
                  }"
                  @click="pageTitle = 'Body Mass Index'"
                  class="dropdown-item"
                  >BMI</router-link
                >
              </li>

              <li>
                <router-link
                  :to="{
                    name: 'calculator',
                    params: { feature: 'calories_need' },
                  }"
                  @click="pageTitle = 'Calories Need Calculator'"
                  class="dropdown-item"
                  >Calories Need</router-link
                >
              </li>
            </ul>
          </li>
          <li class="nav-item">
            <router-link
              :to="{
                name: 'article',
                params: { feature: 'articles' },
              }"
              @click="pageTitle = 'Articles'"
              class="nav-link active"
              aria-current="page"
              >Articles</router-link
            >
          </li>
        </ul>
        <div class="">
          <router-link
            to="/articles"
            @click="logout"
            class="btn btn-danger"
            aria-current="page"
            >Logout</router-link
          >
        </div>
      </div>
    </div>
  </nav>
</template>

<style></style>
