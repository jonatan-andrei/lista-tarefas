<template>
  <div class="row">
    <div>
      <input v-model="task" placeholder="Adicione uma nova tarefa" />
      <button v-on:click="addNewItem">Confirmar</button>
    </div>

    <div class="col-4">
      <h3>First draggable with header</h3>

      <draggable
        id="first"
        data-source="juju"
        :list="list"
        class="list-group"
        draggable=".item"
        group="a"
      >
        <div
          class="list-group-item item"
          v-for="element in list"
          :key="element.name"
        >
          {{ element.name }}
        </div>

        <div
          slot="header"
          class="btn-group list-group-item"
          role="group"
          aria-label="Basic example"
        >
          <button class="btn btn-secondary" @click="add">Add</button>
          <button class="btn btn-secondary" @click="replace">Replace</button>
        </div>
      </draggable>
    </div>

    <div class="col-4">
      <h3>Second draggable with header</h3>

      <draggable :list="list2" class="list-group" draggable=".item" group="a">
        <div
          class="list-group-item item"
          v-for="element in list2"
          :key="element.name"
        >
          {{ element.name }}
        </div>

        <div
          slot="header"
          class="btn-group list-group-item"
          role="group"
          aria-label="Basic example"
        >
          <button class="btn btn-secondary" @click="add2">Add</button>
          <button class="btn btn-secondary" @click="replace2">Replace</button>
        </div>
      </draggable>
    </div>

    <div class="col-4">
      <h3>First draggable with header</h3>

      <draggable
        id="first"
        data-source="juju"
        :list="list3"
        class="list-group"
        draggable=".item"
        group="a"
      >
        <div
          class="list-group-item item"
          v-for="element in list3"
          :key="element.name"
        >
          {{ element.name }}
        </div>

        <div
          slot="header"
          class="btn-group list-group-item"
          role="group"
          aria-label="Basic example"
        >
          <button class="btn btn-secondary" @click="add3">Add</button>
          <button class="btn btn-secondary" @click="replace3">Replace</button>
        </div>
      </draggable>
    </div>

    <rawDisplayer class="col-2" :value="list" title="List" />

    <rawDisplayer class="col-2" :value="list2" title="List2" />

    <rawDisplayer class="col-2" :value="list2" title="List3" />
  </div>
</template>

<script>
import draggable from "vuedraggable";
let id = 1;
export default {
  name: "two-list-headerslots",
  display: "Two list header slot",
  order: 14,
  task: "",
  components: {
    draggable,
  },
  data() {
    return {
      list: [
        { name: "John 1", id: 0 },
        { name: "Joao 2", id: 1 },
        { name: "Jean 3", id: 2 },
      ],
      list2: [
        { name: "Jonny 4", id: 3 },
        { name: "Guisepe 5", id: 4 },
      ],
      list3: [
        { name: "John 1", id: 5 },
        { name: "Joao 2", id: 6 },
        { name: "Jean 3", id: 7 },
      ],
    };
  },
  methods: {
    addNewItem: function () {
      let newTask = this.task;
      if (newTask) {
        this.list.push({ name: newTask, id: id++ });
        this.task = '';
      }
    },
    add: function () {
      this.list.push({ name: "Juan " + id, id: id++ });
    },
    replace: function () {
      this.list = [{ name: "Edgard", id: id++ }];
    },
    add2: function () {
      this.list2.push({ name: "Juan " + id, id: id++ });
    },
    replace2: function () {
      this.list2 = [{ name: "Edgard", id: id++ }];
    },
    add3: function () {
      this.list3.push({ name: "Juan " + id, id: id++ });
    },
    replace3: function () {
      this.list3 = [{ name: "Edgard", id: id++ }];
    },
  },
};
</script>
<style scoped></style>