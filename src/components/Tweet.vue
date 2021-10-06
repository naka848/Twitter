<template>
    <!-- <div>
        <p>{{ tweet }}</p>
    </div> -->
    <!-- 配列を受け取って分解したい -->
    <!-- <ul>
        <li v-for="hensu in hairetu">
            {{ hensu }}
        </li>
    </ul> -->
    <slot />
</template>

<script>
export default {
    name: 'Tweet',
    props : {
        tweet: String,
        // 配列の定義ってどうするんだ？
    },
}
</script>
