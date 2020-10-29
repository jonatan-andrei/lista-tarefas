<template>
  <div class="template">
    <div class="row">
      <div class="title">Lista de Tarefas</div>
    </div>

    <div>
      <div class="row input-group form-add-task">
        <input
          type="text"
          class="form-control"
          v-model="task"
          placeholder="Adicione uma nova tarefa"
        />
        <div class="input-group-prepend">
          <button class="btn btn-outline-secondary" v-on:click="addNewItem">
            Confirmar
          </button>
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col-4 list-tasks">
        <h3 class="title-tasks">A fazer</h3>

        <draggable :list="list" class="list-group" draggable=".item" group="a">
          <div
            class="list-group-item item new-tasks tasks"
            v-for="element in list"
            :key="element.name"
          >
            {{ element.name }}
          </div>
        </draggable>
      </div>

      <div class="col-4 list-tasks">
        <h3 class="title-tasks">Em andamento</h3>

        <draggable
          :list="pending"
          class="list-group"
          draggable=".item"
          group="a"
        >
          <div
            class="list-group-item item pending-tasks tasks"
            v-for="element in pending"
            :key="element.name"
          >
            {{ element.name }}
          </div>
        </draggable>
      </div>

      <div class="col-4 list-tasks">
        <h3 class="title-tasks">Concluído</h3>

        <draggable :list="done" class="list-group" draggable=".item" group="a">
          <div
            class="list-group-item item done-tasks tasks"
            v-for="element in done"
            :key="element.name"
          >
            {{ element.name }}
          </div>
        </draggable>
      </div>
    </div>

    <rawDisplayer class="col-2" :value="list" title="List" />

    <rawDisplayer class="col-2" :value="pending" title="Pending" />

    <rawDisplayer class="col-2" :value="done" title="Done" />
  </div>
</template>

<script>
import draggable from "vuedraggable";
let id = 1;
export default {
  name: "lista-tarefas",
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
      pending: [
        { name: "Jonny 4", id: 3 },
        { name: "Guisepe 5", id: 4 },
      ],
      done: [
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
        this.task = "";
      }
    },
  },
};
</script>
<style scoped>
.template {
  margin: 20px;
  height: 100vh;
}
.title {
  text-align: center;
  margin: 0 auto;
  padding: 30px;
  font-family: "Comic Sans MS", "Comic Sans", cursive;
  color: green;
  font-size: 50px;
}
.form-add-task {
  max-width: 600px;
  margin: 0 auto;
}
.tasks {
  margin: 5px;
  min-height: 50px;
  min-width: 300px;
  color: white;
  text-align: center;
  font-size: 20px;
}
.title-tasks {
  text-align: center;
}
.list-tasks {
  padding: 50px;
}
.list-group .new-tasks {
  background-color: blue;
}
.list-group .pending-tasks {
  background-color: orangered;
}
.list-group .done-tasks {
  background-color: green;
}
</style>