
<template>
  <!-- partial:index.partial.html -->
  <div class="flex-container">
    <div class="flex-slide Write">
      <div class="flex-title flex-title-home">Write</div>
      <div class="flex-about flex-about-home">
        <h2>Leave a Note...</h2>

        <form>
          <textarea placeholder="write..." v-model="neww">
                        </textarea>
          <span id="comment" @click="sss()">Comment</span>
        </form>
      </div>
    </div>
    <div class="flex-slide about">
      <div class="flex-title">Preview</div>
      <div class="flex-about">
        <h2>Preview notes</h2>
        <form v-for="item in previewdata">
          <textarea id="previewnotes" v-model="item.body" readonly>
                  	</textarea>
          <span id="Delete">Delete</span>
          <span id="Edit">Edit</span>
        </form>

      </div>
    </div>
  </div>
</template>

<script >
import axios from 'axios'

export default {

  data() {
    return {
      previewdata: [
        // { text: 'this is text 1' },
        // { text: 'this is text 2' }
      ],
      neww: '',

    }


  },
  created() {
        axios.get("https://crub-744dc-default-rtdb.firebaseio.com/news").then(({ data }) => {
          console.log(data);
        //     const dataa = Object.entries(data).map(([title, body]) => {
        //         return {
        //             title,
        //             ...body
        //         };
        //     })
        //     this.previewdata = dataa
         }
        )
        .catch("check your connection")
    },
  methods: {

    sss() {
      axios.post("https://crub-744dc-default-rtdb.firebaseio.com/news.json", { name: 'ali' }).then(res => { console.log(res) }
      );



      // let newnote = {
      //   done: true,
      //   text: this.neww
      // }
      // axios.post("https://crub-744dc-default-rtdb.firebaseio.com/news.json", this.newnote)
      //   .then(res => {
      // console.log(res)
      // this.previewdata.push({
      //   ...newnote
    }


    //   ).catch(err => {
    //     console.log(err);
    //   }
    //   )
    // }
  }
}



$(".flex-slide").each(function () {
  $(this).hover(function () {
    $(this).find('.flex-title').css({
      transform: 'rotate(0deg)',
      top: '10%'
    });
    $(this).find('.flex-about').css({
      opacity: '1'
    });
  }, function () {
    $(this).find('.flex-title').css({
      transform: 'rotate(90deg)',
      top: '15%'
    });
    $(this).find('.flex-about').css({
      opacity: '0'
    });
  })
});

</script>


