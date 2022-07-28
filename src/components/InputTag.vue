<script>
    export default {
        data() {
            return {
                currentValue: '',
                tags: [
                    'dormir',
                    'estudiar'
                ]                
            }
        },
        methods: {
            handleKeyDown(e) {
                if (e.key === 'Enter' && this.currentValue !== '') {
                    if (!this.tags.includes(this.currentValue)) {
                        this.tags = [...this.tags, this.currentValue]
                    }
                    this.currentValue = ''
                }
                if (e.key === 'Backspace' && this.currentValue === '') {
                    this.tags.pop()
                }
            },
            deleteTag(tag) {
                this.tags = this.tags.filter(value => value !== tag)
            }
        }
    }
</script>

<template>
    <div class="input-tag">
        <div class="tags">
            <div v-for="(tag,index) in tags" :key="index">
                {{tag}}
                <button @click="deleteTag(tag)">x</button>
            </div>            
        </div>
        <input type="text" v-model="currentValue" @keydown="handleKeyDown" />
    </div>
</template>

<style scoped>
    .input-tag {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 5px 13px;
        border: 2px solid rgb(209, 148, 33);
        border-radius: 30px;
        max-width: 90vw;
        overflow-x: hidden;
    }

    .tags {
        display: flex;
        gap: 10px;  
    }

    .tags div {
        border: 1px solid lightgray;
        padding: 3px;
        display: flex;
        align-items: center;
        gap: 5px;
    }

    .tags div button {
        border: none;
        outline: none;
        font-weight: bolder;
        color: rgb(209, 148, 33);
        cursor: pointer;
    }

    input {
        border: none;
        outline: none;
        margin-left: 10px;
        width: 100px;
        background-color: transparent;
    }
</style>