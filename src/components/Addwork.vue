<template>
  <v-container>
    <v-card class="mx-auto" max-width="600">
      <h1 class="text-center purple" :style="{ color }">{{ title }}</h1>

      <form class="mt-5">
        <v-select
          class="px-15"
          v-model="select"
          :items="subject"
          label="Subject"
        ></v-select>
        <v-text-field
          v-model="addtodo"
          class="px-15"
          label="Work"
          :rules="rules"
          hide-details="auto"
        ></v-text-field>
        <v-card-actions class="d-flex justify-center mt-5">
          <v-btn depressed color="success" @click="addworkTodo"> ADD </v-btn>

          <v-btn depressed color="red accent-4" @click="resetTodo">
            RESET
          </v-btn>
        </v-card-actions>
      </form>
    </v-card>

    <v-card class="mx-auto" max-width="600">
      <v-container rounded class="text-center mt-5 purple"
        ><h2 class="white--text">Work Todo</h2></v-container
      >
      <v-container class="d-flex justify-space-between">
        <div class="ml-4"><h3>Subject</h3></div>
        <div class="mr-10"><h3>Namework</h3></div>
        <div class="mr-1"><h3>Delete</h3></div>
      </v-container>
    </v-card>

    <v-card
      class="mx-auto mt-2"
      max-width="600"
      outlined
      v-for="(item, i) in addtitem"
      :key="i"
    >
      <v-list-item>
        <v-container class="d-flex justify-space-between">
          <v-list-item-content>
            <v-list-item-title v-text="item.text"></v-list-item-title>
          </v-list-item-content>
          <v-list-item-content>
            <v-list-item-title v-text="item.listtodo"></v-list-item-title>
          </v-list-item-content>

          <v-btn fab dark x-small color="red" @click="deleteTodo(i)">
            <v-icon dark> mdi-minus </v-icon>
          </v-btn>
        </v-container>
      </v-list-item>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: "Header",
  props: ["title", "color"],
  data: () => ({
    select: "",
    addtodo: "",
    subject: ["Subject Web", "Subject SA", "Subject ML", "ETC"],
    addtitem: [],
    rules: [(value) => !!value || "Please insert your homework"],
  }),
  methods: {
    addworkTodo() {
      this.addtitem.push({
        text: this.select,
        listtodo: this.addtodo,
      });
    },
    deleteTodo(i) {
      this.addtitem.splice(i, 1);
    },
    resetTodo() {
      this.addtodo = "";
      this.select = "";
    },
  },
};
</script>

<style></style>
