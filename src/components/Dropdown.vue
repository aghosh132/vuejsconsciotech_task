<template>
  <nav>
    <ul class="main-nav">
      <li v-for="el in navLinksData" :key="el.id">
        <a
          :href="el.url"
          class="header-nav-link"
          :class="{
            'options-hover': el.children,
          }"
        >
          <span>{{ el.name }}</span>
        </a>
        <ul
          v-if="el.children"
          class="header-nav-ul"
          :class="{
            'open': showSubMenu[el.id],
            'closed': !showSubMenu[el.id],
          }"
        >
          <li
            v-for="child in el.children"
            :key="child.id"
            class="sub-menu-li"
          >
            <a
              :href="child.url"
              class="sub-menu-link"
              style="text-decoration: none"
            >
              <span>{{ child.name }}</span>
            </a>
          </li>
        </ul>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {

  name: "Dropdown",
  props: {
    navLinksData: {
      type: Array,
      default: [],
    },
  },
  data() {
    return {
      showSubMenu: [],
    };
  },
  methods: {
    onSubMenuEnter(subMenuId) {
      this.showSubMenu[subMenuId] = true;
    },
    onSubMenuLeave(subMenuId) {
      this.showSubMenu[subMenuId] = false;
    },
  },
};
</script>
