<template>
    <div>
        <ul class="bg-white p-10 absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2">
            <span @click="$emit('closePopup')" class="absolute top-1 right-1 text-red-500 cursor-pointer">X</span>
            <li>{{ dataOfDisplayedUser.name }}</li>
            <li>{{ dataOfDisplayedUser.username }}</li>
            <li>{{ dataOfDisplayedUser.phone }}</li>
            <li>{{ dataOfDisplayedUser.email }}</li>
            <li>{{ dataOfDisplayedUser.website }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        dataOfDisplayedUser: {
            type: Object,
            required: true,
        }
    }
}
</script>