<template>
  {{ title }}
  <form @submit.prevent="doSubmit">
    <div v-for="(item, index) in data" :key="index">
      <span>{{ item.type }}</span>
      <input
        type="number"
        step="any"
        v-for="(j, idx) in item.projects"
        :key="idx"
        v-model="j.value"
        class="cell"
      />
    </div>
    <input type="submit" value="Submit" />
  </form>
</template>

<script>
export default {
  mounted() {
    this.clone = Object.assign({}, this.data)
  },
  methods: {
    doSubmit() {
      console.log(this.data)
    }
  },
  data: () => {
    return {
      title: 'Grid Form',
      clone: null,
      data: [
        {
          type: 'Barn',
          projects: [
            { class: '1a', value: 201 },
            { class: '2a', value: 202 },
            { class: '3a', value: 203 },
            { class: '4a', value: 204 }
          ]
        },
        {
          type: 'House',
          projects: [
            { class: '1a', value: 301 },
            { class: '2a', value: 302 },
            { class: '3a', value: 303 },
            { class: '4a', value: 304 }
          ]
        },
        {
          type: 'Theater',
          projects: [
            { class: '1a', value: 401 },
            { class: '2a', value: 402 },
            { class: '3a', value: 403 },
            { class: '4a', value: 404 }
          ]
        }
      ]
    }
  }
}
</script>

<style scoped>
span {
  margin: 0 5px;
}
.cell:focus {
  outline: red solid 3px;
  border: 0px;
}

/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type='number'] {
  -moz-appearance: textfield;
}
</style>
