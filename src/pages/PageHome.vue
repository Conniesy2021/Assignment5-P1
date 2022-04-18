<template>
   <q-page class="relative-position">
    <q-scroll-area class="absolute fullscreen">
    <div class="q-py-lg q-px-md row items-end q-col-gutter-md">
        <div class="col">
          <q-input
            v-model="newQweetContent"
            placeholder="What's happening?"
            counter
            maxlength="280"
            botton-slots
            autogrow
            class="new-queet"
          >
          <template v-slot:before>
            <q-avatar size="xl">
            <img :src="require('assets/avatar5.jpg')" alt="">
          </q-avatar>
          </template>

          </q-input>
        </div>

        <div class="col col-shrink">
            <q-btn
              @click="addNewQweet"
              :disable="!newQweetContent"
              class="q-mb-lg"
              unelevated
              rounded
              color="primary"
              label="Queet"
              no-caps />
        </div>
      </div>
      <q-separator size="15px" color="pink-2" class="divider" />

      <q-list separator>
        <transition-group
        appear
          enter-active-class="animated fadeIn"
          leave-active-class="animated fadeOut"
      />

          <q-item
            v-for="qweet in qweets"
            :key="qweet.date"
            class="q-py-md">

            <q-item-section avatar top>
              <q-avatar>
                <img :src="require('assets/avatar5.jpg')" alt="">
              </q-avatar>
            </q-item-section>

            <q-item-section>
              <q-item-label><strong> Connie </strong>  </q-item-label>
              <q-item-label class="qweet-content"> {{ qweet.content}}
              </q-item-label>
                <div class="row justify-between q-mt-sm">
                  <q-btn
                    flat
                    round
                    color="pink"
                    icon="far fa-comment"/>

                  <q-btn
                    flat
                    round
                    color="pink"
                    icon="fas fa-retweet"/>

                    <q-btn
                    flat
                    round
                    color="pink"
                    icon="far fa-heart"/>

                    <q-btn
                    flat
                    round
                    color="pink"
                    icon="fas fa-trash"/>

              </div>
              </q-item-section>
            <q-item-section side top>
              {{ qweet.date}}

            </q-item-section>


          </q-item>
      </q-list>


    </q-scroll-area>
  </q-page>
</template>


  <script>
  export default {
    name: 'PageHome',
    data() {
      return {
        newQweetContent: '',
        qweets: [
                  {
                    content:  'There are two primary choices in life: to accept conditions as they exist, or accept the responsibility for changing them',
                    date: 20210101
                  },
                  {
                    content:  'Aerodynamically the bumblebee shouldnt be able to fly but the bumblebee doesnt know that so it goes on flying anyway',
                    date: 20220102
                  },
                   {
                    content:  'To be or not to be, this is a question',
                    date: 20220201
                  },
                  {
                    content:  'Do not aim for success if you want it; just do what you love and believe in, and it will come naturally.',
                    date: 20220312
                  },
                  {
                    content:  'You cannot improve your past, but you can improve your future. Once time is wasted, life is wasted.',
                    date: 20220316
                  },
                ]

      }
    },


    methods:{
      addNewQweet() {
        let newQweet = {
          content: this.newQweetContent,
          date: Date.now()
        }
        this.qweets.unshift(newQweet)
        this.newQweetContent = ''
    }

    }

  }
  </script>

  <style lang ="sass">
    .divider
      border-top: 1px solid
      border-bottom: 1px solid

    .new-qweet
      textarea
        font-size: 15px
        line-height: 1.6 !important
        border-color: grey-4
    .qweet-content
      white-space: pre-line

  </style>



