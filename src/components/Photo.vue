<template>
  <div>
  <h1 class="ml-10 mt-15">{{ msg }}</h1>
  <v-layout wrap cols="4" sm="12" class="mt-10 px-10 justify-space-between ">
    <v-card v-for="photo in photos" :key="photo.title" class="mb-5">
      <p class="text-center my-5">{{ photo.title }}</p>
      <v-img :src="photo.url"></v-img>
    </v-card>
  </v-layout>
  
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'Photo',
      photos: [
      //新幹線
      {
        title: '新幹線での様子',
        url: 'https://1.bp.blogspot.com/-CZhDpH9AENw/WTd5T6ADZtI/AAAAAAABEuw/epxCOLW9e0QvxnGxHjquTneZkhotr294gCLcB/s400/travel_bus_train_student.png'
      },
      //富士山
      {
        title: '富士山',
        url: 'https://3.bp.blogspot.com/-WiNPt0_l3lc/U0pTNIhcmUI/AAAAAAAAfF4/BW1m-kFqMzI/s400/fujisan_shikaku.png' 
      },
      //夕日
      {
        title: '夕日',
        url: 'https://3.bp.blogspot.com/-WiNPt0_l3lc/U0pTNIhcmUI/AAAAAAAAfF4/BW1m-kFqMzI/s400/fujisan_shikaku.png' 
      }
    ]
    }
  }
}
</script>