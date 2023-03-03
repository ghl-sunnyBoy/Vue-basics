<template>
    <ul class="todo-list">
        <li :class="{ completed: v.isDeno }" v-for="v in list" :key="v.id">
            <div class="view">
                <input class="toggle" type="checkbox" v-model="v.isDeno" />
                <label>{{ v.name }}</label>
                <button class="destroy" @click="$emit('del', v.id)"></button>
            </div>
        </li>
    </ul>
</template>

<script>
export default {
    props: {
        list: Array
    }
}
</script>