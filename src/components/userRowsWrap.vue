<template>
    <div class="relative">
        <usersSortBar @sortBy="sortResultsBy"></usersSortBar>
        <userSingleRow 
            v-for="user in filteredUsers" 
            :key="user.id"
            :user="user"
            @showPopup = "showPopup"
        />
        <userSinglePopup v-if="Boolean(currentVisibleUser)" :dataOfDisplayedUser="currentVisibleUser" @closePopup="closePopup"/>
    </div>
</template>

<script>
import userSingleRow from './userSingleRow.vue'
import userSinglePopup from './userSinglePopup.vue'
import usersSortBar from './usersSortBar.vue'

import axios from 'axios';

export default {
    components: {
        userSingleRow,
        userSinglePopup,
        usersSortBar,
    },
    data() {
        return {
            users: [],
            filteredUsers:[],
            currentVisibleUser: null,
        }
    },
    mounted() {
        this.getUsersFromDatabase()
    },
    methods: {
        async getUsersFromDatabase() {
            try {
                const response = await axios.get('https://jsonplaceholder.typicode.com/users')
                this.users = response.data
                this.filteredUsers = response.data
            } catch (error) {
                console.error(error)
            }
        },
        getSpecificUserFromList(searchBy, searchQuery) {
            const filteredUsersList = this.users.filter((user)=> {
                const userPropertyLowerCase = user[searchBy].toLowerCase()
                return userPropertyLowerCase.startsWith(searchQuery)
            })
            this.filteredUsers = filteredUsersList
        },
        sortResultsBy(type, order) {
            if(order === 'descending') {
                this.filteredUsers.sort((a, b) => (a[type] > b[type]) ? 1 : -1)
            } else {
                this.filteredUsers.sort((a, b) => (a[type] > b[type]) ? -1 : 1)
            }
            
        },
        showPopup(userData) {
            this.currentVisibleUser = userData
        },
        closePopup(){
            this.currentVisibleUser = null
        }
    }
}
</script>