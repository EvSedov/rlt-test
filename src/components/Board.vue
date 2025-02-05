<script setup lang="ts">
import { onBeforeMount, ref } from "vue";

import Cell from "./Cell.vue";
import DragElement from "./DragElement.vue";
import CardDetailedInformation from "./CardDetailedInformation.vue";

import ItemFirst from "/src/assets/img/ItemFirst.png";
import ItemSecond from "/src/assets/img/ItemSecond.png";
import ItemThird from "/src/assets/img/ItemThird.png";
import ItemsToDelete from "./ItemsToDelete.vue";

interface IElement {
  id: number;
  cellId: number;
  count: number;
  name: string;
  icon: string;
  description: string;
}

const cells = ref<{ id: number }[]>([
  { id: 1 },
  { id: 2 },
  { id: 3 },
  { id: 4 },
  { id: 5 },
  { id: 6 },
  { id: 7 },
  { id: 8 },
  { id: 9 },
  { id: 10 },
  { id: 11 },
  { id: 12 },
  { id: 13 },
  { id: 14 },
  { id: 15 },
  { id: 16 },
  { id: 17 },
  { id: 18 },
  { id: 19 },
  { id: 20 },
  { id: 21 },
  { id: 22 },
  { id: 23 },
  { id: 24 },
  { id: 25 },
]);

const selectedItem = ref<IElement | null>(null);
const startPositionElements = ref<IElement[]>([
  {
    id: 1,
    cellId: 1,
    name: "Element 1",
    icon: ItemFirst,
    description:
      "Описание предмета с названием Element 1. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dignissimos, tempore!",
    count: 4,
  },
  {
    id: 2,
    cellId: 2,
    name: "Element 2",
    icon: ItemSecond,
    description:
      "Описание предмета с названием Element 2. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dignissimos, tempore!",
    count: 2,
  },
  {
    id: 3,
    cellId: 3,
    name: "Element 3",
    icon: ItemThird,
    description:
      "Описание предмета с названием Element 3. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dignissimos, tempore!",
    count: 5,
  },
]);
const currentPositionElements = ref<IElement[]>([]);
const localStorageKey = "currentPositionElements";

const deleteItemShow = ref<boolean>(false);
const countForDelete = ref<number>(0);

const selectItem = (item: IElement) => {
  selectedItem.value = item;
  console.log({ item: selectedItem.value });
};

const startDragElement = (event: DragEvent, element: IElement) => {
  event.dataTransfer!.dropEffect = "move";
  event.dataTransfer!.effectAllowed = "move";
  event.dataTransfer!.setData("elementId", element.id.toString());
  console.log({ element, index: event.dataTransfer!.getData("elementId") });
};

const dropElement = (elementId: number, cellId: number) => {
  currentPositionElements.value = currentPositionElements.value.map(
    (item: IElement) => {
      if (item.id === elementId) {
        item.cellId = cellId;
      }
      return item;
    }
  );
  localStorage.setItem(
    localStorageKey,
    JSON.stringify(currentPositionElements.value)
  );
  console.log({ elementId, cellId });
};

const showItemToDelete = () => {
  deleteItemShow.value = true;
};

const cancelDeletion = () => {
  deleteItemShow.value = false;
  selectedItem.value = null;
  countForDelete.value = 0;
};

const confirmDeletion = () => {
  if (countForDelete.value <= 0) {
    cancelDeletion();
    return;
  }

  if (selectedItem.value && countForDelete.value > selectedItem.value?.count) {
    selectedItem.value.count = 0;
  } else if (selectedItem.value) {
    selectedItem.value.count = selectedItem.value.count - countForDelete.value;
  }

  if (selectedItem.value && selectedItem.value.count === 0) {
    currentPositionElements.value = currentPositionElements.value.filter(
      (item: IElement) => item.id !== selectedItem.value!.id
    );

    cancelDeletion();
    return;
  }

  currentPositionElements.value.map((item: IElement) => {
    if (selectedItem.value && item.id === selectedItem.value.id) {
      item = selectedItem.value;
    }

    return item;
  });

  cancelDeletion();
};

onBeforeMount(() => {
  currentPositionElements.value = JSON.parse(
    localStorage.getItem(localStorageKey) || "[]"
  );
  currentPositionElements.value = currentPositionElements.value.length
    ? currentPositionElements.value
    : startPositionElements.value;
  localStorage.setItem(
    localStorageKey,
    JSON.stringify(currentPositionElements.value)
  );
});
</script>

<template>
  <div class="board">
    <Cell
      v-for="cell in cells"
      :key="`${cell.id}`"
      :cellId="cell.id"
      :element="cell"
      @drop-cell="(elementId: number) => dropElement(elementId, cell.id)"
    >
      <DragElement
        v-for="element in currentPositionElements.filter((el: IElement) => el?.cellId === cell.id)"
        :id="element.id"
        :srcIcon="element.icon"
        :name="element.name"
        :draggable="true"
        @dragstart="startDragElement($event, element)"
        @click="selectItem(element)"
      />
    </Cell>
    <CardDetailedInformation
      v-if="selectedItem"
      :element="selectedItem"
      class="cardDetailedInformation"
      @deleting="showItemToDelete"
    />
    <ItemsToDelete
      v-if="deleteItemShow"
      v-model:count-to-delete="countForDelete"
      class="itemToDelete"
      @cancellation="cancelDeletion"
      @confirmation="confirmDeletion"
    />
  </div>
</template>

<style scoped>
.board {
  position: relative;
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(5, 100px);
  border: 1px solid var(--color-background-thirdly);
  border-radius: var(--radius);
  overflow: hidden;
}

.cardDetailedInformation {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 100;
}

.itemToDelete {
  position: absolute;
  bottom: 0;
  right: 0;
  z-index: 200;
}
</style>
