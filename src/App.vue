<template>
  <div>
    <ul>
      <li v-for="(item, idx) in items" :key="idx">
        {{ item.name }} - {{ item.price }}
      </li>
    </ul>
    <button @click="addAndUpdate">Add and update</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      items: [
        { name: "Alph", price: 1 },
        { name: "Beta", price: 2 },
      ],
    };
  },

  methods: {
    addAndUpdate() {
      const newItem = { name: "New", price: "-" };
      this.items.push(newItem);
      const createdElm = this.items[this.items.length - 1];
      setTimeout(() => {
        // выведет Proxy
        console.log(this.items);
        createdElm.price = "over 9000";
        // подход vue 2 не сработает объект возвращаемой функцией data -
        // это не объект с геттерами/сеттерами, это объект обернутый в Proxy
        // newItem.price = "over 9000";

        this.items[0].foo = 'baz';
      }, 3000);
    },
  },
};
</script>
