<template>
  <div class='ui centered card'>
    <div class="content"v-show="!isEditing">
      <div class='ui center aligned header' style=" color: #808080;">
          {{ todo.title }}
      </div>
      <div class="meta">
          <span class="right floated time">{{ date.dayNum }}.  {{ date.month }}</span>
        </div>
      <div class='description'>
          <form class="ui form"><textarea style="color:  #808080;" rows="3" readonly="true">{{ todo.project }}</textarea></form>
      </div>
      <div class='extra content'>
          <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
        </span>
        <span class="right floated trash icon" v-on:click="deleteTodo(todo)">
        	<i class="trash icon"></i>
        </span>
      </div>
    </div>
<div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="todo.title" >
        </div>
        <div class='field'>
          <label>Description</label>
          <input type='text' v-model="todo.project" >
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">
            Submit
          </button>
        </div>
      </div>
    </div>
    <div class='ui bottom attached green button' style="background-color: #d9ffce; color: #808080;" v-on:click="completeTodo(todo)" v-show="!isEditing &&todo.done" disabled>
        Completed &nbsp <i class="check icon"></i>
    </div>
    <div class='ui bottom attached red button' style="background-color: #ff8b8b; color: #808080;" v-on:click="completeTodo(todo)" v-show="!isEditing && !todo.done">
        Pending
    </div>
  </div>
</template>

<script>
  import moment from 'moment'
	export default {
		props: ['todo'],
		data() {
			return {
				isEditing: false,
        date: {
          dayNum: '',
          month: '',
          year: '',
          dayName: ''
        }
			}
		},
    mounted() {
      this.getCurrentDay();
    },
		methods: {
			showForm() {
				this.isEditing = true;
			},
			hideForm() {
				this.isEditing = false;
			},
			deleteTodo(todo) {
				this.$emit('delete-todo', todo);
			},
			completeTodo(todo) {
				this.$emit('complete-todo', todo);
			},
      getCurrentDay() {
        const today = new Date()
        let dayName = moment(today).format('dddd')
        let [monthDay, year] = moment().format('ll').split(',')
        let [month, day] = monthDay.split(' ')

        this.date.dayNum = day
        this.date.month = month
        this.date.year = year
        this.date.dayName = dayName
      }
		}
	}
</script>

<style scoped>
</style>