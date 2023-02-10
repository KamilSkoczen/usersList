<template>
    <div>
        <ul @click="$emit('showPopup', user)" class="flex flex-row justify-between border-b-4">
            <li>{{ user.id }}</li>
            <li>{{ user.name }}</li>
            <li>{{ user.email }}</li>
        </ul>
    </div>
</template>

<script>
export default {
 props: {
    user: {
        type: Object,
        required: true,
    }
 }
}
</script>