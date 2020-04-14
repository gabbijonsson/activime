<template>
<div class="content">
    <div class="listdisplay-container--activitylist">
        <h1>AKTIVITETSLISTA</h1>
        <button class="listdisplay-container--activitylist--addnewbtn">LÄGG TILL NY</button>
        <ul>
            <li class="listdisplay-container listdisplay-container--activity" v-for="activity in activitylist" :key="activity.id">
                <p>{{ activity.title }}</p>
                <div class="listdisplay-container--btncontainer"><button class="listdisplay-container--activitylist--changebtn"> ÄNDRA </button>
                <button class="listdisplay-container--activitylist--deletebtn"> TA BORT </button></div>
            </li>
        </ul>
    </div>
    <div class="listdisplay-container--worklist">
        <h1>ARBETSUPPGIFTER</h1>
        <button class="listdisplay-container--worklist--addnewbtn">LÄGG TILL NY</button>
        <ul>
            <li class="listdisplay-container listdisplay-container--work" v-for="worktask in worklist" :key="worktask.id">
                <p>{{ worktask.title }}</p>
                <div class="listdisplay-container--btncontainer"><button class="listdisplay-container--worklist--changebtn"> ÄNDRA </button>
                <button class="listdisplay-container--worklist--deletebtn"> TA BORT </button></div>
            </li>
        </ul>
    </div>
</div>

</template>

<script>
export default {
    name: 'ListDisplay',
    data: () => ({
        activitylist: [
            { 
                title: 'Lunch',
                id: 1,
                description: 'Laga och ät lunch',
                allowedInterval: {
                    startHour: '10',
                    startMinute: '30',
                    endHour: '13',
                    endMinute: '15'
                },
                pausLength: 45,
                weatherCondition: 3
            }, 
            { 
                title: 'Kaffepaus',
                id: 2,
                description: 'Gå och ta en kaffe',
                allowedInterval: {
                    startHour: '09',
                    startMinute: '15',
                    endHour: '15',
                    endMinute: '15'
                },
                pausLength: 10,
                weatherCondition: 3
            }, 
            { 
                title: 'Stretchpass',
                id: 3,
                description: 'Sträck ordentligt på armar, ben och rygg!',
                allowedInterval: {
                    startHour: '08',
                    startMinute: '15',
                    endHour: '17',
                    endMinute: '15'
                },
                pausLength: 10,
                weatherCondition: 3
            },
            { 
                title: 'Inomhusvandring',
                id: 4,
                description: 'Gå runt inomhus, stanna inte förrän tiden är slut',
                allowedInterval: {
                    startHour: '08',
                    startMinute: '15',
                    endHour: '16',
                    endMinute: '15'
                },
                pausLength: 15,
                weatherCondition: 2
            },
            { 
                title: 'Promenad',
                id: 5,
                description: 'Ta en promenad utomhus',
                allowedInterval: {
                    startHour: '08',
                    startMinute: '15',
                    endHour: '16',
                    endMinute: '15'
                },
                pausLength: 20,
                weatherCondition: 1
            }
        ],
        worklist: [
            { 
                title: 'Inköpsorder A4-papper',
                id: 1,
            }, 
            { 
                title: 'Fakturagodkännanden',
                id: 2,
            }, 
            { 
                title: 'Leverantörsfakturor',
                id: 3,
            },
            { 
                title: 'Lönelistor',
                id: 4,
            },
            { 
                title: 'Kontoavstämning',
                id: 5,
            }
        ]
    })
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

.listdisplay-container--activitylist, .listdisplay-container--worklist {
    max-width: 1000px;
    margin: auto;
}

.listdisplay-container--worklist {
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