<template>
    <div class="pb-6 flex flex-row items-center">
        <h2 class="text-base pr-2">choose item to search by:</h2>
        <select class="px-2 border-2 border-black" name="search-type" id="search-type" ref="searchBySelect" @change="getSearchSelectValue()">
            <option value="name">name</option>
            <option value="email">email</option>
        </select>
        <input @input="$emit('searchUser', searchBy, searchQuery)" type="text" class="border-2 border-black mx-2 px-2" v-model="searchQuery" placeholder="type here...">
        <button @click="$emit('searchUser', searchBy, searchQuery)" class="bg-black text-white p-2 rounded"> search </button>
        
    </div>
</template>

<script>

export default {
    data() {
        return {
            searchQuery: '',
            searchBy: '',
        }
    },
    mounted() {
        this.getSearchSelectValue()
    },
    methods: {
        getSearchSelectValue() {
            this.searchBy = this.$refs.searchBySelect.value
        },
    }
}
</script>