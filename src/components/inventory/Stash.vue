<template>
  <div class="stash">
    <div class="btn-group" role="group">
      <button
          type="button"
          class="btn btn-secondary"
          :class="{ active: activeTab == 1 }"
          @click="changeTab(1)"
      >
        Personal
      </button>
      <button
          type="button"
          class="btn btn-secondary"
          :class="{ active: activeTab == 2 }"
          @click="changeTab(2)"
      >
        Shared
      </button>
      <button
          type="button"
          class="btn btn-secondary"
          :class="{ active: activeTab == 3 }"
          @click="changeTab(3)"
      >
        Shared
      </button>
      <button
          type="button"
          class="btn btn-secondary"
          :class="{ active: activeTab == 4 }"
          @click="changeTab(4)"
      >
        Shared
      </button>
    </div>
    <!-- переключатель D2R/D2R-BLIZZ -->
    <!-- <div class="mode-toggle">
      <div class="btn-group">
        <button
            type="button"
            class="btn btn-outline-secondary"
            :class="{ active: gameMode === 'd2r' }"
            @click="gameMode = 'd2r'"
        >
          LoD
        </button>
        <button
            type="button"
            class="btn btn-outline-secondary"
            :class="{ active: gameMode === 'd2r-blizz' }"
            @click="gameMode = 'd2r-blizz'"
        >
          D2R
        </button>
      </div>
    </div>-->
    <div class="stash-bg":class="{'stash-bg-big': gameMode === 'd2r-blizz'}">
      <Grid
          v-if="activeTab == 1"
          :width="stashGrid.width"
          :height="stashGrid.height"
          :page="1"
          :items.sync="stash(0)"
          @item-selected="onSelect"
          @item-event="onEvent"
          :id="'Grid'"
          :contextMenu="contextMenu"
          class="y-0"
      ></Grid>
      <Grid
          v-if="activeTab == 2"
          :width="stashGrid.width"
          :height="stashGrid.height"
          :page="2"
          :items.sync="stash(1)"
          @item-selected="onSelect"
          @item-event="onEvent"
          :id="'Grid'"
          :contextMenu="contextMenu"
          class="y-0"
      ></Grid>
      <Grid
          v-if="activeTab == 3"
          :width="stashGrid.width"
          :height="stashGrid.height"
          :page="3"
          :items.sync="stash(2)"
          @item-selected="onSelect"
          @item-event="onEvent"
          :id="'Grid'"
          :contextMenu="contextMenu"
          class="y-0"
      ></Grid>
      <Grid
          v-if="activeTab == 4"
          :width="stashGrid.width"
          :height="stashGrid.height"
          :page="4"
          :items.sync="stash(3)"
          @item-selected="onSelect"
          @item-event="onEvent"
          :id="'Grid'"
          :contextMenu="contextMenu"
          class="y-0"
      ></Grid>
    </div>
  </div>
</template>

<script>
import Item from './Item.vue';
import Grid from './Grid.vue';
import ContextMenu from "../ContextMenu.vue";

export default {
  name: 'Stash',
  components: {
    Item,
    Grid,
    ContextMenu
  },
  data() {
    return {
      activeTab: 1,
      gameMode: 'd2r-blizz'
    };
  },
  props: {
    items: Array,
    id: String,
    contextMenu: Object,
  },
  computed: {
    stashGrid() {
      return this.gameMode === 'd2r-blizz'
          ? { width: 16, height: 13 }
          : { width: 10, height: 10 };
    }
  },
  methods: {
    onSelect(item) {
      this.$emit('item-selected', item);
    },
    stash(i) {
      if (this.items.pages[i] == null) return [];
      return this.items.pages[i].items || []
    },
    changeTab(i) {
      this.activeTab = i;
    },
  }
}
</script>

<style scoped>
.mode-toggle {
  margin: 10px 0;
  display: flex;
}

/* Стили для активной кнопки переключателя */
.btn-outline-secondary.active {
  background-color: #6c757d;
  color: white;
  border-color: #6c757d;
}
</style>