<template>
  <BContainer fluid>
    <BRow>
      <BCol>
        <BCarousel v-model="modelValue" controls :interval="8000" indicators ride="carousel">
          <BCarouselSlide :interval="2000" img-src="https://picsum.photos/1024/480/?image=13" />
          <BCarouselSlide :interval="4000" img-src="https://picsum.photos/1024/480/?image=14" />
          <BCarouselSlide img-src="https://picsum.photos/1024/480/?image=15" />
        </BCarousel>
        <BCarousel controls :interval="8000" indicators ride="carousel">
          <BCarouselSlide :interval="2000" img-src="https://picsum.photos/1024/480/?image=13" />
          <BCarouselSlide :interval="4000" img-src="https://picsum.photos/1024/480/?image=14" />
          <BCarouselSlide img-src="https://picsum.photos/1024/480/?image=15" />
        </BCarousel>
        <BCarousel
          id="carousel-1"
          :interval="4000"
          controls
          indicators
          background="#ababab"
          img-width="1024"
          img-height="480"
          style="text-shadow: 1px 1px 2px #333"
        >
          <!-- Text slides with image -->
          <BCarouselSlide
            active
            caption="First slide"
            text="Nulla vitae elit libero, a pharetra augue mollis interdum."
            img-src="https://picsum.photos/1024/480/?image=52"
          />

          <!-- Slides with custom text -->
          <BCarouselSlide img-src="https://picsum.photos/1024/480/?image=54">
            <h1>Hello world!</h1>
          </BCarouselSlide>

          <!-- Slides with image only -->
          <BCarouselSlide img-src="https://picsum.photos/1024/480/?image=58" />

          <!-- Slides with img slot -->
          <!-- Note the classes .d-block and .img-fluid to prevent browser default image alignment -->
          <BCarouselSlide>
            <template #img>
              <img
                width="1024"
                height="480"
                src="https://picsum.photos/1024/480/?image=55"
                alt="image slot"
              />
            </template>
          </BCarouselSlide>

          <!-- Slide with blank fluid image to maintain slide aspect ratio -->
          <BCarouselSlide caption="Blank Image" img-blank img-alt="Blank image">
            <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse eros felis,
              tincidunt a tincidunt eget, convallis vel est. Ut pellentesque ut lacus vel interdum.
            </p>
          </BCarouselSlide>
        </BCarousel>
      </BCol>
    </BRow>
    <BRow>
      <BCol>
        <BCarousel>
          <BCarouselSlide
            v-for="(image, index) in images"
            :key="index"
            :img-src="image"
            img-alt="Image alt text"
          >
            <h1>Image {{ index + 1 }}</h1>
            <p>Some more detailed description or whatever content.</p>
          </BCarouselSlide>
        </BCarousel>
      </BCol>
    </BRow>
  </BContainer>
</template>

<script setup lang="ts">
import {ref} from 'vue'

const modelValue = ref(0)
const images = ref(['https://picsum.photos/1024/480/?image=55'])

const newValue = [
  'https://picsum.photos/1024/480/?image=56',
  'https://picsum.photos/1024/480/?image=57',
  'https://picsum.photos/1024/480/?image=58',
  'https://picsum.photos/1024/480/?image=59',
  'https://picsum.photos/1024/480/?image=60',
  'https://picsum.photos/1024/480/?image=61',
  'https://picsum.photos/1024/480/?image=62',
  'https://picsum.photos/1024/480/?image=63',
  'https://picsum.photos/1024/480/?image=64',
  'https://picsum.photos/1024/480/?image=65',
  'https://picsum.photos/1024/480/?image=66',
  'https://picsum.photos/1024/480/?image=67',
  'https://picsum.photos/1024/480/?image=68',
  'https://picsum.photos/1024/480/?image=69',
]

setTimeout(() => {
  images.value = [images.value[0], ...newValue]
}, 1000)
</script>
