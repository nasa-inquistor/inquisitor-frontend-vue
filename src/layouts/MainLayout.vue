<template>
  <q-layout view="hHh lpR fFf">
    <q-header class="bg-white text-primary">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <img src="../assets/logo.png" width="213" height="49" />
        </q-toolbar-title>
        <div></div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      :width="200"
      :breakpoint="500"
    >
      <q-list>
        <q-item-label header class="label-menu"> Explorar </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
        <q-item-label header class="label-menu"> Projetos </q-item-label>
        <EssentialLink
          v-for="linkPersonal in personalLinks"
          :key="linkPersonal.title"
          v-bind="linkPersonal"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from "vue";
import EssentialLink from "src/components/EssentialLink.vue";

const leftDrawerOpen = ref(false);

const essentialLinks = ref([
  {
    title: "Projetos",
    icon: "dataset",
    link: "/",
  },
  {
    title: "Pesquisadores",
    icon: "group",
    link: "/",
  },
  {
    title: "Radio",
    icon: "sensors",
    link: "/",
  },
]);

const personalLinks = ref([
  {
    title: "Projeto Biologia",
    icon: "park",
    link: "/",
  },
  {
    title: "Projeto Astronomia",
    icon: "park",
    link: "/",
  },
  {
    title: "Projeto Fisica",
    icon: "park",
    link: "/",
  },
  {
    title: "Projeto Fisica",
    icon: "park",
    link: "/",
  },
  {
    title: "Projeto Computação",
    icon: "park",
    link: "/",
  },
  {
    title: "Cultura de microorganismos",
    icon: "park",
    link: "/",
  },
]);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>

<style scoped>
.label-menu {
  color: #09090b;
  font-size: 1.125rem;
  font-style: normal;
  font-weight: 600;
  line-height: 1.75rem; /* 155.556% */
  letter-spacing: -0.02813rem;
}
</style>
