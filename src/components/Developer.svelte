<script>
    import file from "../file.json";
</script>

<section>
    Data is controlled by external source. Web Tools are developed by
    <a href={file[0].developer}>{file[0].name}</a>, Thanks.
</section>

<style scoped>
    section {
        position: absolute;
        bottom: 0px;
        width: 200px;
        padding: 12px;
    }
    section a {
        text-decoration: none;
        color: #333;
        background-color: #ffffff;
    }
</style>
