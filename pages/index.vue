<template>
<div class="mt-5" style="display:flex;justify-content:center;">
   <div class="text-center mt-5">
   <input type="text" class="form-control text-center mb-3" v-model="todo" placeholder="ketikan sesuatu"/>
    <button type="button" class="btn btn-primary" @click="tambahTodo"> Tambah</button>

    <!-- todolist -->
    <p>todolist :</p>
    <div v-if="isNoTodolist">
      <small>tambahkan data</small>
    </div>
    <ul class="list-group text-center">
    <li v-for="(datalist,i) in todolist" :key="i">

    <div style="display:flex; align-item:center; justify-content:flex-between;">
        <div class="form-check" @click="tambahListDone">
        <input class="form-check-input" type="checkbox" value="" id="defaultCheck1">
        <label class="form-check-label" for="defaultCheck1">
        </label>
        </div>
        {{datalist}}
        <div>
        <i class="fas fa-trash" @click="deleteList"></i>
        </div>
        </div>

    </li>
    </ul>
<!-- cari index yang dipilih -->
<!-- lalu tarik dari todolist dan hapus dari todolist -->
    <!-- listdone -->
    <div class="list-done">
        <p>list done :</p>

        <li v-for="(datadone,i) in listdone" :key="i">
    <div style="display:flex; align-item:center; justify-content:flex-between;">
        
        <div class="form-check">
        <input class="form-check-input" type="checkbox" value="" id="defaultCheck1">
        <label class="form-check-label" for="defaultCheck1">
        </label>
        </div>
        {{datadone}}
        <div>
        <i class="fas fa-trash" @click="deleteListDone"></i>
        </div>
        </div>

    </li>
    </div>
  </div>
  </div>
</template>

<script>
export default {
    layout:"clear",
  data() {
    return {
      todo:"",
      todolist: [],
    listdone: [],
    }
  },
  computed: {
    isNoTodolist() {
      return this.todolist.length == 0 || this.todolist == "";
    }
  },
  methods : {
    tambahTodo() {
    this.todolist.push(this.todo);
    this.todo = "";
  },
    deleteList(datalist) {
      this.todolist.splice(datalist.target.parentNode.parentNode.dataset.index, 1);
    },
    tambahListDone(datalist) {
      this.listdone.push(this.todolist[datalist.target.parentNode.parentNode.dataset.index]);
      this.todolist.splice(datalist.target.parentNode.parentNode.dataset.index, 1);
    },
    deleteListDone(datalist) {
      this.listdone.splice(datalist.target.parentNode.parentNode.dataset.index, 1);
    },
    changeListDone(listdone) {
      this.todolist.push(this.listdone[datalist.target.parentNode.parentNode.dataset.index]);
      this.listdone.splice(datadone.target.parentNode.parentNode.dataset.index, 1);
    }
  },
  
}
</script>
