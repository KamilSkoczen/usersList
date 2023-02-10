<template>
    <div class="max-w-[60%] mx-auto my-10">
        <h1 class="font-bold text-xl pb-6">Users list:</h1>
        <usersSearch @searchUser="getSpecificUser" ref="userSearch"></usersSearch>
        <userRowsWrap ref="userRowsWrap"></userRowsWrap>
    </div>
</template>

<script>
import userRowsWrap from './userRowsWrap.vue'
import usersSearch from './usersSearch.vue'
export default {
    components: {
        userRowsWrap,
        usersSearch,
    },
    methods: {
        getSpecificUser(searchBy,searchQuery) {
            this.$refs.userRowsWrap.getSpecificUserFromList(searchBy,searchQuery)
        }
    }
}
</script>