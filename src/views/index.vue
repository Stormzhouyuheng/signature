<template>
    <my-wrapper fit title="项目模板首页示例">
        <!-- 设计电子签章部分 -->
        <CreateSealsMain></CreateSealsMain>
    </my-wrapper>
</template>

<script>
    import CreateSealsMain from './CreateSeals'
    export default {
        components: {
            CreateSealsMain
        }
    }
</script>
