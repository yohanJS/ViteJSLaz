
<template>
  <section class="bg-light mt-5 mb-5 p-4 shadow-sm" id="reviews">
    <div class="row d-flex justify-content-center">
      <div class="col-md-10 col-xl-8 text-center">
        <h4 class="mb-4 fw-bold">VERIFIED CUSTOMER TESTIMONIALS</h4>
        <p class="mb-4 pb-2 mb-md-5 pb-md-0 text-start">
          At Laz Appliances Repair LLC, we take pride in the feedback from our customers. 
          Each testimonial you read here is a genuine expression of satisfaction from individuals 
          who have experienced our exceptional service. We believe in transparency and trust, and 
          that's why all our testimonials are from verified users. Join the countless others who have 
          chosen Laz Appliances Repair LLC for a reliable and trustworthy experience.
        </p>
      </div>
    </div>

    <!--Carousel-->
    <div class="row justify-content-center">
      <div class="col-md-6">
        <div id="carouselExampleControls" class="carousel slide" data-bs-ride="carousel">
          <div class="carousel-inner">
            <div v-for="(review, index) in reviews" :key="index" class="carousel-item" :class="{ active: index === 0 }">
              <img src="https://mdbcdn.b-cdn.net/img/Photos/Avatars/img%20(1).webp" class="rounded-circle shadow-1-strong"
                width="150" height="150" alt="Reviewer Avatar" />
              <p class="m-0 p-0 mt-5">{{ review.content }}</p>
              <p class="lead mt-2">{{ review.author }}</p>
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="blue" class="bi bi-patch-check-fill"
                viewBox="0 0 16 16">
                <path
                  d="M10.067.87a2.89 2.89 0 0 0-4.134 0l-.622.638-.89-.011a2.89 2.89 0 0 0-2.924 2.924l.01.89-.636.622a2.89 2.89 0 0 0 0 4.134l.637.622-.011.89a2.89 2.89 0 0 0 2.924 2.924l.89-.01.622.636a2.89 2.89 0 0 0 4.134 0l.622-.637.89.011a2.89 2.89 0 0 0 2.924-2.924l-.01-.89.636-.622a2.89 2.89 0 0 0 0-4.134l-.637-.622.011-.89a2.89 2.89 0 0 0-2.924-2.924l-.89.01zm.287 5.984-3 3a.5.5 0 0 1-.708 0l-1.5-1.5a.5.5 0 1 1 .708-.708L7 8.793l2.646-2.647a.5.5 0 0 1 .708.708" />
              </svg>
              <span class="fw-bold"> verified customer</span>
              <div class="stars">
                <!-- Use the SVG star icon five times for the rating -->
                <svg v-for="star in 5" :key="star" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16" fill="none"
                  stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"
                  class="star-icon">
                  <polygon
                    points="8 1 10.09 4.26 14 5.27 11 8.64 12.18 11.52 8 9.27 3.82 11.52 5 8.64 1 5.27 5.91 4.26 8 1" />
                </svg>
              </div>
            </div>
          </div>
          <button class="carousel-control-prev mb-5" type="button" data-bs-target="#carouselExampleControls"
            data-bs-slide="prev">
            <span class="carousel-control-prev-icon bg-dark" aria-hidden="true"></span>
            <span class="visually-hidden">Previous</span>
          </button>
          <button class="carousel-control-next mb-5" type="button" data-bs-target="#carouselExampleControls"
            data-bs-slide="next">
            <span class="carousel-control-next-icon bg-dark" aria-hidden="true"></span>
            <span class="visually-hidden">Next</span>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
// Import axios
import axios from 'axios';

export default {
  data() {
    return {
      reviews: [],
    };
  },
  methods: {
    async fetchData() {
      try {
        // Using axios
        const response = await axios.get('https://www.bloggyapi.com/blogpost');
        this.reviews = response.data;
        //console.log(this.reviews);
      } catch (error) {
        console.error('Error fetching reviews:', error);
      }
    },
  },
  mounted() {
    // Call fetchData method when the component is mounted (page load)
    this.fetchData();
  },
};
</script>

<style>
.star-icon {
  width: 12px;
  /* Adjust the size as needed */
  height: 12px;
  margin-right: 2px;
  /* Adjust spacing between stars */
  fill: gold;
  /* Customize the star color */
}
</style>
