<template>
<div>
    <h3>{{weatherFive.list[0].visibility}}</h3>
</div>
</template>

<script>
export default {
    name: 'FiveDay',
    props: {
        weatherFive: Object,
    }
}
</script>