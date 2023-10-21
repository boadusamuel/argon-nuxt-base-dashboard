<template>
  <div
      id="sidenav-collapse-main"
      class="collapse navbar-collapse w-auto h-auto h-100"
  >
    <ul class="navbar-nav">
      <li class="nav-item">
        <SidenavCollapse
            collapse-ref="dashboardsExamples"
            nav-text="Dashboards"
            :class="getRoute === 'dashboards' ? 'active' : ''"
        >
          <template #icon>
            <i class="ni ni-shop text-primary text-sm opacity-10"></i>
          </template>
          <template #list>
            <ul class="nav ms-4">
              <SidenavItem
                  to="/dashboards/default"
                  mini-icon="D"
                  text="Default"
              />
            </ul>
          </template>
        </SidenavCollapse>
      </li>
      <li class="mt-3 nav-item">
        <h6
            class="text-xs ps-4 text-uppercase font-weight-bolder opacity-6"
            :class="isRTL ? 'me-4' : 'ms-2'"
        >
          PAGES
        </h6>
      </li>
      <li class="nav-item">
        <sidenav-collapse collapse-ref="apiExamples" nav-text="Examples (API)"
                          :class="getRoute === 'examples' ? 'active' : ''">
          <template #icon>
            <i class="fab fa-vuejs text-success text-sm opacity-10"></i>
          </template>
          <template #list>
            <ul class="nav ms-4">
              <SidenavItem to="/examples/user-profile" mini-icon="U" text="User Profile"/>
              <SidenavItem to="/examples/user-management/list-users" mini-icon="U" text="User Management"/>
            </ul>
          </template>
        </sidenav-collapse>
      </li>
      <li class="nav-item d-flex align-items-center">
        <SidenavItem to="/pages/charts" mini-icon="C" text="Charts">
          <i class="ni ni-chart-bar-32 text-warning text-sm opacity-10"></i>
        </SidenavItem>
      </li>

      <li class="nav-item d-flex align-items-center">
        <SidenavItem to="/applications/data-tables" mini-icon="D" text="Data Tables">
          <i class="ni ni-align-left-2 text-info text-sm opacity-10"></i>
        </SidenavItem>
      </li>
      <li class="nav-item d-flex align-items-center">
        <SidenavItem to="/pages/widgets" mini-icon="W" text="Widgets">
          <i class="ni ni-ungroup text-success text-sm opacity-10"></i>
        </SidenavItem>
      </li>

    </ul>
  </div>
  <div class="mt-3 sidenav-footer">
  </div>
</template>
<script setup>
import SidenavCollapse from "./SidenavCollapse.vue";
// import SidenavCollapseItem from "./SidenavCollapseItem.vue";
import SidenavItem from "./SidenavItem.vue";
import {useNavStore} from "~~/stores/NavStore";

const navStore = useNavStore();

const sidenavType = computed(() => {
  return navStore.sidenavType === "bg-white" ? "text-dark" : "text-white";
});
const getRoute = computed(() => {
  const route = useRoute();
  return route.path.split("/")[1];
});
defineProps({
  isRTL: {
    type: Boolean,
    default: false,
  },
});
</script>
