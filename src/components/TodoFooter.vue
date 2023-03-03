<template>
    <footer class="footer">
        <span class="todo-count">剩余<strong>{{ list.length }}</strong></span>
        <ul class="filters">
            <li>
                <a :class="{ selected: comm === '全部' }" @click="change('全部')" href="javascript:;">全部</a>
            </li>
            <li>
                <a :class="{ selected: comm === '未完成' }" @click="change('未完成')" href="javascript:;">未完成</a>
            </li>
            <li>
                <a :class="{ selected: comm === '已完成' }" @click="change('已完成')" href="javascript:;">已完成</a>
            </li>
        </ul>
        <button class="clear-completed" @click="$emit('clear')">清除已完成</button>
    </footer>
</template>

<script>

export default {
    props: {
        list: Array
    },
    data() {
        return {
            comm: '全部'
        }
    },
    methods: {
        change(v) {
            this.comm = v
            this.$emit('change', this.comm)
        }
    }

};
</script>