<template>
    <div>
        <h2 class="title">Registrar fotos</h2>
        <Button
            type="button"
            label="Save"
            class="button--primary"
        />
    </div>
</template>
<script>
import Button from '../../components/button/Button';
export default {
    components:{
        Button: Button
    }
}
</script>
<style lang="css" scoped>
    .title {
        text-align: center;
    }
</style>