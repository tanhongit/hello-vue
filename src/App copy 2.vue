<template>
  <!--root element -->
  <div id="app">
    <div>
      <h1 :class="{ daChon: selected }">lap trinh vien</h1>
      <button @click="selected = !selected">Doi mau</button>

      <hr />
      <input type="text" :disabled="inputDisabled" />
      <button @click="inputDisabled = !inputDisabled">Mo khoa</button>
      <!--chu y co : -->
    </div>

    <hr />
    <div>
      <input type="text" v-model="changemane" />
      {{ changemane }}
    </div>

    <hr />
    <div>
      <input type="text" v-model="changemanes[0]" />
      <input type="text" v-model="changemanes[1]" />
      {{ changemanes }}
    </div>

    <hr />
    <div>
      <input type="text" v-model="channel.name" />
      {{ channel.name }}
    </div>

    <hr />
    <div>
      <input type="text" v-model="channel.name" />
      <button v-on:click="channel.name = 'Aaaaaa'">Go</button>
      <button v-on:mouseover="channel.name = 'Aaaaaa'">Go</button>
    </div>

    <hr />
    <div>
      <form action="/abc">
        <input type="text" v-model="channel.name" />
        <button type="submit" v-on:click.prevent="channel.name = 'Aaaaaa'">
          Send
        </button>
      </form>
    </div>

    <hr />
    <div>
      <div v-if="isShow">Lap trinh vien</div>
      <button @click="isShow = !isShow">
        <span v-if="isShow">An</span>
        <span v-else>Hien</span>
      </button>
    </div>

    <hr />
    <div>
      <div v-for="(index, task) in tasks" :key="index">
        {{ task }} - {{ index }}
      </div>
    </div>

    <hr />
    <div>
      <div v-for="(task, index) in tasks2" :key="index">
        <input type="checkbox" v-model="task.done" />
        <span :class="{ done: task.done }">{{ task.content }}</span>
      </div>
    </div>

    <hr />
    <div>
      <input type="text" v-model="newTask" />
      <button @click="tasks2.push({ content: newTask, done: false })">
        Add
      </button>
      <div v-for="(task, index) in tasks2" :key="index">
        <input type="checkbox" v-model="task.done" />
        <span :class="{ done: task.done }">{{ task.content }}</span>
      </div>
    </div>

    <!-- ------------------------- -->
    <!-- method -->
    <hr />
    <div>
      <input type="text" v-model="newTask" />
      <button @click="addTask()">Add</button>
      <div v-for="(task, index) in task3" :key="index">
        <input type="checkbox" v-model="task.done" />
        <span :class="{ done: task.done }">{{ task.content }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputDisabled: true,
      isShow: true,
      selected: true,
      changemane: "Gau gau",
      changemanes: ["Gau gau 1", "Gau gau 2"],

      channel: {
        //object
        name: "Gau gau",
      },

      tasks: ["di choi", "nau an", "code", "di ve sinh"],

      tasks2: [
        { content: "di choi", done: false },
        { content: "nau an", done: false },
        { content: "code", done: false },
        { content: "di ve sinh", done: false },
      ],

      newTask: "",

      task3: [],
    };
  },

  methods: {
    addTask: function () {
      this.task3.push({
        content: this.newTask,
        done: false,
      });
    },
  },

  watch:{
    newTask: function(){
      console.log('new task change');
    }
  },

  mounted(){

  }
};
</script>

<style>
.daChon {
  color: red;
}
.done {
  text-decoration: line-through;
}
</style>
