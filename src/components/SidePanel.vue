<template>
  <div class="SidePanel">
    <div class="SidePanel__header">
      <WorkatoLink class="button button_link button_block" href="/recipes/new">
        <i class="fas fa-plus"></i>
        New recipe
      </WorkatoLink>
    </div>
    <div class="SidePanel__separator"></div>
    <div class="SidePanel__content">
      <WorkatoLink class="SidePanel__item" activeClass="SidePanel__item_active" href="/dashboard/main"
        :activeOn="['/dashboard*']">
        Dashboard
      </WorkatoLink>
      <WorkatoLink class="SidePanel__item" activeClass="SidePanel__item_active" href="/"
        :activeOn="['/recipes*']"
        :inactiveOn="['/recipes/browse*']">
        Recipes
      </WorkatoLink>
      <WorkatoLink class="SidePanel__item" activeClass="SidePanel__item_active" href="/connections"
        :activeOn="['/connections*']">
        Connected Apps
      </WorkatoLink>
      <WorkatoLink class="SidePanel__item" activeClass="SidePanel__item_active" href="/recipes/browse"
        :activeOn="['/recipes/browse*']">
        Community
      </WorkatoLink>
    </div>
  </div>
</template>

<script>
  import WorkatoLink from "@/components/WorkatoLink";

  export default {
    name: "SidePanel",
    components: { WorkatoLink }
  }
</script>

<style lang="scss">
  .SidePanel {
    background: #F3F4F6;
    height: 100%;

    &__header {
      margin: 25px 47px 25px 25px;
    }

    &__separator {
      display: block;
      content: "";
      height: 3px;
      background: #DFDFDE;
      margin: 25px 47px 25px 15px;
    }

    &__item {
      display: block;
      border-left: 4px solid transparent;
      padding: 8px 45px 8px;
      font-size: 14px;

      &,
      &:link,
      &:visited,
      &:hover,
      &:active {
        text-decoration: none;
      }

      &,
      &:link,
      &:visited,
      &:hover,
      &:active {
        color: #37434C;
      }

      &_active {
        border-left-color: #37434c;
        background: #DADFE3;
        font-weight: bold;
      }
    }
  }
</style>
