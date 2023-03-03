<template>
    <div class="todoapp">
        <todo-header @add="add" :list="list"></todo-header>
        <todo-main :list="newList" @del="del"></todo-main>
        <todo-footer :list="list" @clear="clear" @change="change"></todo-footer>
    </div>
</template>

<script>

import TodoHeader from './components/TodoHeader.vue';
import TodoMain from './components/TodoMain.vue';
import TodoFooter from './components/TodoFooter.vue';
export default {
    components: {
        TodoFooter,
        TodoMain,
        TodoHeader,
    },
    data() {
        return {
            list: JSON.parse(localStorage.getItem('commit')) || [
                { id: 1, name: 321, isDeno: false }
            ],
            v: ''
        }
    },
    methods: {
        // 添加
        add(value) {
            this.list.push({
                id: Date.now(), name: value, isDeno: false
            })
        },
        // 删除
        del(id) {
            this.list = this.list.filter(x => x.id != id)
        },
        // 清除已完成
        clear() {
            this.list = this.list.filter(x => !x.isDeno)
        },
        change(v) {
            this.v = v
        }
    },
    watch: {
        list: {
            deep: true,
            handler() {
                localStorage.setItem('commit', JSON.stringify(this.list))
            }
        }
    },
    computed: {
        newList() {
            if (this.v === '已完成') {
                return this.list.filter(x => x.isDeno)
            } else if (this.v === '未完成') {
                return this.list.filter(x => !x.isDeno)
            } else {
                return this.list
            }
        }
    }
}
</script>

<style scoped></style>