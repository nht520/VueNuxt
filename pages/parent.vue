<template>
    <div>
        <p>我是parent</p>
        <!-- sc快速生成命令 -->
        <ul>
            <li>
                <nuxt-link to="/parent/class">classs</nuxt-link>
            </li>
            <li>
                <nuxt-link to="/parent/about">about</nuxt-link>
            </li>
        </ul>
        <nuxt-child></nuxt-child>
    </div>
</template>
<script>
    export default {
        name:"parent"
    }
</script>

<style>

</style>
