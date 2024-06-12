<template>
    <div class="createSealsMain">
        <SealButtons/>
        <CreateSealsPanel/>
    </div>
</template>

<script>
import SealButtons from '@/components/SealButtons'
import CreateSealsPanel from '@/components/CreateSealsPanel'
export default {
    components: {
        SealButtons,
        CreateSealsPanel
    }
}
</script>

<style lang="scss" scoped>
.createSealsMain {
    width: 100%;
    // height: 760px;
    padding: 0 20px;
    background: #e8e8ea;
}
</style>
