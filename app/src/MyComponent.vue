<template>
  <div class="list-body">

    <h2  v-bind:style="{}" v-bind:class="notes.length > 5 ?'first':'second'">Список Заміток:</h2>
    <input class="list-body" type="text"
           v-bind:placeholder="clue"
           v-model="inputValue"
           v-on:keypress.enter="addNewNotes"
    />
    <div v-if="notes.length !==0"> Плани на сьогодні :
      <ol>
        <li class="list-style"
            v-bind:class="notes.length > 5 ?'yellow':'green'" v-for="(oneNote,index) in notes" v-bind:key="index">{{oneNote}}
          <br>
          <button class="btn" v-on:click="deleteNotes(index)">Видалити!</button>
        </li>
      </ol>
    </div>

    <ol v-else-if="notes.length !==0">
      <li v-for="(oneNote,index) in notes" v-bind:key="index">{{oneNote}}
        <br>
        <button v-on:click="deleteNotes(index)">Видалити</button>
      </li>
    </ol>
    <div v-else>Немає ніяких Планів на сьогодні</div>
  </div>
</template>
<script>
export default {
  data (){
    return{
      clue:'Вести список планів : ',
      inputValue:"",
      notes:[]
    }
  },
  methods : {
    addNewNotes(){
      this.notes.push(event.target.value);
      this.inputValue = ''
    },
    deleteNotes(index){
      this.notes.splice(index,1)

    }
  }
}
</script>
<style>
.list-body{
  padding: 10px 0;
  border: 1px solid green;
  border-radius: 25px;
  text-align: center;
  width: 600px;
  margin: 0 auto;



}
.list-body{
  margin-bottom: 20px;
}
.first{
  color: red;
}
.second{
  color: #6bf66b;
}
.green{
  background: #6bf66b;

}
.yellow{
  background: red;
}
.color{
  background: blueviolet;
}
.btn{
  margin-top: 10px;
  background-color: #008CBA;
  border: none;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
.list-style{
  margin-bottom: 10px;
}
</style>
