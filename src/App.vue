
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
              {{ newnote }}
              {{ previewdata }}
          <span id="comment" @click="sss()">Comment</span>
        </form>
      </div>
    </div>
    <div class="flex-slide about">
      <div class="flex-title">Preview</div>
      <div class="flex-about">
        <h2>Preview notes</h2>
        <form>
          <textarea placeholder="write..." id="previewnotes" v-model="previewdata" readonly>
        				</textarea>
          <span id="Delete">Delete</span>
          <span id="Edit">Edit</span>
        </form>
        <form>
          <textarea :key="index" placeholder="write..." id="previewnotes" readonly>
        				</textarea>
          <span id="Delete">Delete</span>
          <span id="Edit">Edit</span>
        </form>
      </div>
    </div>
  </div>
</template>

<script >
export default {
  data() {
    return {
      previewdata: [
      ],
      neww : '',
      newnote: ''
    }


  },
  methods: {
    sss() {
      this.newnote = this.neww
      this.previewdata.push(newnote)
    }
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


