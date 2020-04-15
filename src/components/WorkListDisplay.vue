<template>
<div class="content">
    <div class="listdisplay-container--worklist">
        <h1>ARBETSUPPGIFTER</h1>
        <div class="listdisplay-container--worklist-addnew">
            <input v-model="newWorkTaskTitle" placeholder="Ange arbetsuppgift här"/>
            <button class="listdisplay-container--worklist--addnewbtn" @click="addNewWorkTask(newWorkTaskTitle)">LÄGG TILL NY</button>
        </div>
        <ul>
            <li class="listdisplay-container listdisplay-container--work" v-for="worktask in worklist" :key="worktask.id">
                <p>{{ worktask.title }}</p>
                <div class="listdisplay-container--btncontainer">
                <button class="listdisplay-container--worklist--deletebtn" @click="removeWorkTask(worktask.id)"> TA BORT </button></div>
            </li>
        </ul>
    </div>
</div>

</template>
<script>
import {eventBus} from "../main";
export default {
    name: 'WorkListDisplay',
    data: () => ({
        newWorkTaskTitle: '',
        defaultWorklist: [
            { 
                title: 'Inköpsorder A4-papper',
                id: 1,
                finished: false
            }, 
            { 
                title: 'Fakturagodkännanden',
                id: 2,
                finished: false
            }, 
            { 
                title: 'Leverantörsfakturor',
                id: 3,
                finished: false
            },
            { 
                title: 'Lönelistor',
                id: 4,
                finished: false
            },
            { 
                title: 'Kontoavstämning',
                id: 5,
                finished: false
            }
        ],
        worklist: []
    }),  
    created(){
        eventBus.$emit('workList', this.worklist);
        let savedWorkList = JSON.parse(localStorage.getItem('worklist'));
        if (savedWorkList && savedWorkList.length > 0) {
            this.worklist = savedWorkList;
        } else {
            this.worklist = this.defaultWorklist;
            this.saveToLocalStorage(this.defaultWorklist);
        }
    },
    methods: {
            saveToLocalStorage: function (optionalList) {
                let listToSave = optionalList ? optionalList : this.worklist;
                localStorage.setItem('worklist', JSON.stringify(listToSave))
            },
            removeWorkTask: function (id) {
                console.log('id ' + id)
                let index = this.worklist.findIndex((workTask) => workTask.id === id);
                console.log('index ' + index);
                this.worklist.splice(index, 1);
                console.log('worklist is ' + this.worklist)
                this.saveToLocalStorage()
            },
            addNewWorkTask: function (newTaskTitle) {
                let newId = this.worklist.length > 0 ? this.worklist[this.worklist.length-1].id+1 : 1;
                let newTask = {
                    title: newTaskTitle,
                    id: newId,
                    finished: false
                }
                this.worklist.push(newTask)
                this.saveToLocalStorage()
            },            
            sendList(){
            eventBus.$emit('workList', this.worklist)
        }
    }  
}

</script>

<style scoped>
* {
    list-style: none;
}
.content {
  margin-top: 5em;
}
ul {
    padding: 0;
}
li {
    margin-top: 2em;
}

p {
    font-size: 2em;
    align-self: center;
}

.listdisplay-container--worklist {
    max-width: 1000px;
    margin: auto;
    margin-bottom: 6em;
}

.listdisplay-container--btncontainer {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
}

.listdisplay-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto;
    column-gap: 2em;
    margin-left: 3em;
    margin-right: 3em;
}

button {
  background-color: #77c9d4;
  width: 10em;
  height: 3em;
  border-radius: 20px;
  border: 0em;
  box-shadow: 1px 6px #999;
  font-weight: 600;
  font-size: 18px;
  cursor: pointer;
  margin: 0.5em;
}

</style>