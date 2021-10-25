<template>
  <div class="m-5">
    <div class="card">
      <div class="card-header bg-white">
        {{ TweetObj.tweet_user.user_name }} @
        {{ TweetObj.tweet_user.user_id }}
      </div>
      <div class="card-body">
        {{ TweetObj.tweet_body }}
      </div>
      <!-- ♡をクリック→iineCountイベント発生 -->
      <div class="card-footer bg-white">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="16"
          height="16"
          fill="currentColor"
          class="bi bi-heart item"
          viewBox="0 0 16 16"
          v-on:click="iineCount"
        >
          <path
            d="m8 2.748-.717-.737C5.6.281 2.514.878 1.4 3.053c-.523 1.023-.641 2.5.314 4.385.92 1.815 2.834 3.989 6.286 6.357 3.452-2.368 5.365-4.542 6.286-6.357.955-1.886.838-3.362.314-4.385C13.486.878 10.4.28 8.717 2.01L8 2.748zM8 15C-7.333 4.868 3.279-3.04 7.824 1.143c.06.055.119.112.176.171a3.12 3.12 0 0 1 .176-.17C12.72-3.042 23.333 4.867 8 15z"
          />
        </svg>
        {{ count }}
        
        <!-- viewBox="x, y, width, height"
          x,yは左上からみたx座標とy座標の位置、そしてwidth,heightは描画エリアの幅(座標値)と高さ(座標値) -->
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="16"
          height="16"
          fill="currentColor"
          class="bi bi-arrow-left-right item"
          viewBox="0 0 16 16"
        >
          <path
            fill-rule="evenodd"
            d="M1 11.5a.5.5 0 0 0 .5.5h11.793l-3.147 3.146a.5.5 0 0 0 .708.708l4-4a.5.5 0 0 0 0-.708l-4-4a.5.5 0 0 0-.708.708L13.293 11H1.5a.5.5 0 0 0-.5.5zm14-7a.5.5 0 0 1-.5.5H2.707l3.147 3.146a.5.5 0 1 1-.708.708l-4-4a.5.5 0 0 1 0-.708l4-4a.5.5 0 1 1 .708.708L2.707 4H14.5a.5.5 0 0 1 .5.5z"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Tweet",
  props: {
    TweetObj: Object,
  },
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    iineCount() {
      this.count++;
    },
  },
};
</script>
