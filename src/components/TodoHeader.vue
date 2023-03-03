<template>
    <header class="header">
        <h1>todos</h1>

        <input id="toggle-all" class="toggle-all" type="checkbox" v-model="ckAll" />
        <label for="toggle-all"></label>
        <input class="new-todo" placeholder="输入任务名称-回车确认" autofocus v-model="value" @keyup.enter="add" />
    </header>
</template>

<script>

export default {
    data() {
        return {
            value: '',
        }
    },
    props: {
        list: Array
    },
    methods: {
        add() {
            if (this.value === '') {
                return alert('内容不能为空')
            }
            this.$emit('add', this.value)
            this.value = ''
        }
    },
    computed: {
        ckAll: {
            get() {
                return this.list.every(x => x.isDeno)
            },
            set(ck) {
                // this.$emit('chAll', ck)
                this.list.forEach(x => x.isDeno = ck)
            }
        }
    }
}
</script>