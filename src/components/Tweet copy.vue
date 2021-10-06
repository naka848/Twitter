<template>
    <div>
        <p>{{ tweet }}</p>
    </div>
</template>

<script>
export default {
    name: 'Tweet',
    props : {
        tweet: String,
    },
}
</script>
