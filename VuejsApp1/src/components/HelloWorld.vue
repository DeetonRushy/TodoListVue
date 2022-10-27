<script setup>
import {ref} from 'vue'

const statisticPanel = ref(false)
    const statistics = [
        {
            stat: "Total Items",
            value: 0
        },
        {
            stat: "Total Items Completed",
            value: 0
        },
        {
            stat: "Total Items Skipped",
            value: 0
        }
    ]

    const STAT_ITEMS = 0
    const STAT_COMPLETED = 1
    const STAT_SKIPPED = 2

    const items = ref([])
    const inputBox = ref('')

    const showingNotification = ref(false)
    const notification = ref('')

    const showNotification = (message) => {
        notification.value = message
        showingNotification.value = true
        setInterval(function () {
            showingNotification.value = false
            notification.value = ''
        }, 5000)
    }

    const addItem = () => {

      if (inputBox.value === ""){
        showNotification("you must enter a name");
        return
      }

      const obj = {
            title: inputBox.value,
            done: false
        }
        items.value.push(obj)
        inputBox.value = ''

        statistics[STAT_ITEMS].value++
    }
    const removeItem = (index) => {
        items.value.splice(index, 1)
    }
    const forceRemoveItem = (index) => {
        items.value.splice(index, 1)
        statistics[STAT_SKIPPED].value++
    }
    const itemComplete = (index) => {
        items.value[index].done = true
        statistics[STAT_COMPLETED].value++
    }

    const clearAllItems = () => {
        if (items.value.length === 0) {
            showNotification("nothing to remove!")
            return
        }

        // this map call doesn't really work, need to read more into how it works.
        // Im assuming it's like C#'s LINQ array.Where(x => <condition>)...
        statistics[STAT_SKIPPED].value += items.value.map(x => { return x.done === true }).length
        items.value = []
    }
</script>

<template>
  <div>
      <input id="add-item" type="text" placeholder="enter an item" v-model="inputBox"/>
      <button @click="addItem">Add item</button>
      <button @click="statisticPanel = !statisticPanel">Show Stats</button>
      <button @click="clearAllItems">Clear all items</button>

      <div v-if="statisticPanel === true" class="stat-panel">
          <div v-for="item in statistics" class="stat">
              <p>{{ item.stat }}</p>
              <hr class="rounded" />
              <p> {{item.value}} </p>
          </div>
      </div>

      <div v-if="showingNotification === true" id="notification" class="stat">
          {{ notification }}
      </div>

      <div class="todolist-container">
          <div v-if="items.length === 0" class="cb-item">
              Enter some items!
          </div>
        <ul class="list-items" id="todolist">
            <li class="cb-item" v-for="(item, index) in items" :key="index">
                <div>
                    <p :class="item.done ? 'item-finished' : 'item-progress'">
                        {{ item.title }}
                    </p>
                    <hr v-if="item.done" class="rounded-complete"/>
                    <hr v-else class="rounded-progress"/>
                    <button v-if="!item.done" @click="itemComplete(index)">Complete</button>
                    <button v-if="item.done" @click="removeItem(index)">Remove</button>
                    <button v-if="!item.done" @click="forceRemoveItem(index)">Skip</button>
                </div>
            </li>
        </ul>
      </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
      msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

input[type=text], button {
    font-family: 'Cascadia Code', ui-monospace;
    font-size: 1.5rem;
    font-weight: bold;
}

hr.rounded {
    border-top: 8px solid #bbb;
    border-radius: 3px;
}

hr.rounded-complete {
    border-top: 8px solid #73ff51;
    border-radius: 3px;
}

hr.rounded-progress {
    border-top: 8px solid #ff0000;
    border-radius: 3px;
}

.list-items {
    position: absolute;
    display: flex;
    flex-wrap: wrap;
}

.stat-panel {
    position: relative;
    display: flex;
    flex-wrap: wrap;
}

.stat {
    box-sizing: border-box;
    flex: 1 0 250px;
    margin: 1rem;
    padding: 1rem;
    border: 1px solid #000;
    border-radius: 5px;
    background-color: #475B5A;
    font-family: 'Cascadia Code', ui-monospace;
    color: #73ff51;
    font-size: 1.5rem;
    font-weight: bold;
}

.cb-item {
    box-sizing: border-box;
    flex: 1 0 250px;
    margin: 1rem;
    padding: 1rem;
    border: 1px solid #000;
    border-radius: 5px;
    background-color: #475B5A;
    font-family: 'Cascadia Code',ui-monospace;
    color: white;
    font-size: 1.5rem;
    font-weight: bold;
}

.item-finished {
    text-decoration: line-through solid;
}

.item-progress {
    text-decoration: grammar-error;
    padding: 0.1px;
    margin: 4px
}

.todolist-container {
    margin-top: auto;
}

</style>
