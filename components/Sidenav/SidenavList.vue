<template>
  <div
      id="sidenav-collapse-main"
      class="collapse navbar-collapse w-auto h-auto h-100"
  >
    <ul class="navbar-nav">
      <li class="nav-item d-flex align-items-center">
        <SidenavSingleItem :is-active="getRoute === '/dashboards/default'" to="/dashboards/default" text="Dashboard">
          <i class="ni ni-shop text-primary text-sm opacity-10"></i>
        </SidenavSingleItem>
      </li>


      <li class="nav-item">
        <sidenav-collapse collapse-ref="apiExamples" nav-text="Examples (API)"
                          :class="getRoute === '/examples/user-profile' ? 'active' : '' || getRoute === '/examples/user-management/list-users' ? 'active' : ''">
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
      <li class="nav-item d-flex align-items-center" >
        <SidenavSingleItem  to="/pages/charts" :is-active="getRoute === '/pages/charts'" text="Charts">
          <i class="ni ni-chart-bar-32 text-warning text-sm opacity-10"></i>
        </SidenavSingleItem>
      </li>

      <li class="nav-item d-flex align-items-center">
        <SidenavSingleItem :is-active="getRoute === '/applications/data-tables'" to="/applications/data-tables" text="Data Tables">
          <i class="ni ni-align-left-2 text-info text-sm opacity-10"></i>
        </SidenavSingleItem>
      </li>
      <li class="nav-item d-flex align-items-center">
        <SidenavSingleItem :is-active="getRoute === '/pages/widgets'" to="/pages/widgets" text="Widgets">
          <i class="ni ni-ungroup text-success text-sm opacity-10"></i>
        </SidenavSingleItem>
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
  console.log(route.path)
  return route.path

});
defineProps({
  isRTL: {
    type: Boolean,
    default: false,
  },
});
</script>
