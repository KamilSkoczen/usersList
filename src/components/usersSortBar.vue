<template>
    <ul class="flex flex-row justify-between bg-stone-500 text-slate-100">
        <li class="cursor-pointer" @click="changeSoritngOrder('idOrder'), $emit('sortBy', 'id', idOrder)">ID</li>
        <li class="cursor-pointer" @click="changeSoritngOrder('nameOrder'), $emit('sortBy', 'name', nameOrder)">Name</li>
        <li class="cursor-pointer" @click="changeSoritngOrder('emailOrder'), $emit('sortBy', 'email', emailOrder)">Email</li>
    </ul>
</template>

<script>
export default {
    data(){
        return {
            idOrder:'ascending',
            nameOrder:'descending',
            emailOrder:'descending'
        }
    },
    methods: {
        changeSoritngOrder(property) {
            if(this[property] === 'ascending') {
                this[property] = 'descending'
            } else if (this[property] === 'descending') {
                this[property] = 'ascending'
            } else {
                this[property] = 'ascending'
            }
        }
    }
}
</script>