<template>
    <div id="root">
        <button @click="getStudents">获取学生信息</button>
        <button @click="getCars">获取汽车信息</button>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'App',
    methods: {
        getStudents() {
            axios.get('//localhost:8080/atguigu/students').then(
                response => {
                    console.log('请求成功了', response.data);
                },
                error => {
                    console.log('请求失败了', err.message);
                }
            )
        },
        getCars() {
            axios.get('//localhost:8080/demo/Cars').then(
                response => {
                    console.log('请求成功了', response.data);
                },
                error => {
                    console.log('请求失败了', err.message);
                }
            )
        }
    },
}
</script>

