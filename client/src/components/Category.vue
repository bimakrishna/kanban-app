<template>
  <div>
    <div class = "container-navbar">
        <div class = "item-box flexbox-item-1 rounded mt-2">{{kategoriDetail.kategori}}</div>
    </div>
     <div class="black mt-2 rounded"></div>
        <div class = "category"> 
        <div class="card" style="width: 18rem;">
    <div class="card-body anyClass">
        <TodoList
            v-for="task in taskperKategori"
            :key="task.id"
            :task="task"
            @toEditPage="toEditPage"
            @destroy="destroy"
        >
        </TodoList>
    </div>
        </div>
        </div>
  </div>
</template>

<script>
import TodoList from './TodoList'
export default {
    name: 'Category',
    components: {
        TodoList
    },
    props: ['kategoriDetail', 'tasks'],
    computed: {
        taskperKategori() {
            return this.tasks.filter(task => task.category === this.kategoriDetail.kategori)
            console.log(tasks)
        }
    },
    methods: {
        toEditPage(payload) {
            this.$emit('toEditPage', payload)
        },
        destroy(hapus) {
            this.$emit('destroy', hapus)
        }
    }
}
</script>

<style>

</style>