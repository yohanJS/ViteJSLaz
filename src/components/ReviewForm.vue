<template>
  <div class="container-fluid pt-5 pb-5 p-3">
    <div class="row d-flex justify-content-center">
      <div class="col-12 col-md-6">
        <form
          class="border border-1 shadow-lg rounded-2 p-3"
          id="reviewForm"
          v-on:submit.prevent="createReview"
        >
        <div class="row">
          <div class="col-12 col-md-6 mt-3 text-start">
            <label class="form-label fw-bold">Full Name</label>
            <input
              required
              class="form-control"
              for="author"
              aria-label="Enter author's name"
              v-model="author"
            />
          </div>
          <div class="col-12 col-md-6 mt-3 text-start">
            <label class="form-label fw-bold">Phone Number</label>
            <input
              required
              class="form-control"
              for="phoneNumber"
              aria-label="Enter phone number"
              v-model="phoneNumber"
              type="tel"
            />
          </div>
          <div class="col-12 mt-3 text-start">
            <label class="form-label fw-bold">Email</label>
            <input
              required
              class="form-control"
              for="email"
              aria-label="Enter email"
              v-model="email"
              type="email"
            />
          </div>
        </div>
        <div class="col-12 mt-3 text-start">
          <label class="form-label fw-bold">Write a review</label>
          <textarea required
            class="form-control"
            for="content"
            aria-label="Write a summary of your service"
            v-model="content"
            rows="6"
            cols="50"
          ></textarea>
        </div>
          <div class="col-12 mt-3">
            <label class="lead fw-bold mt-3 mb-4">Rate your experience</label>
            <br />
            <span style="color: #fecd4c; font-size: 1.8rem;">★★★★★</span>
            <input
              required
              class="form-check-input mt-3"
              aria-label="Rate your service"
              for="rating"
              v-model="rating"
              type="radio"
              id="star5"
              name="rating"
              value="5"
            />
            <br />
            <span class="m-1" style="color: #fecd4c; font-size: 1.8rem;">★★★★</span>
            <input
              required
              class="form-check-input mt-3 mt-3 mt-3"
              aria-label="Rate your service"
              for="rating"
              v-model="rating"
              type="radio"
              id="star4"
              name="rating"
              value="4"
            />
            <br />
            <span class="m-1" style="color: #fecd4c; font-size: 1.8rem;">★★★</span>
            <input
              required
              class="form-check-input mt-3 mt-3 mt-3"
              aria-label="Rate your service"
              for="rating"
              v-model="rating"
              type="radio"
              id="star3"
              name="rating"
              value="3"
            />
            <br />
            <span class="m-1" style="color: #fecd4c; font-size: 1.8rem;">★★</span>
            <input
              required
              class="form-check-input mt-3 mt-3 mt-3"
              aria-label="Rate your service"
              for="rating"
              v-model="rating"
              type="radio"
              id="star2"
              name="rating"
              value="2"
            />
            <br />
            <span class="m-1" style="color: #fecd4c; font-size: 1.8rem;">★</span>
            <input
              required
              class="form-check-input mt-3 mt-3 mt-3"
              aria-label="Rate your service"
              for="rating"
              v-model="rating"
              type="radio"
              id="star1"
              name="rating"
              value="1"
            />
          </div>
          <div class="col-12 text-end mt-2">
            <div class="col-12 text-center">
            <button
              type="submit"
              id="submit"
              class="btn btn-lg rounded-pill btn-color btn-text-color fw-bold mt-5 mb-2"
              style="width: 250px"
            >
              Submit
            </button>
            </div>
            <div class="col-12 text-center">
            <button
              type="reset"
              id="reset"
              class="btn btn-lg rounded-pill btn-danger fw-bold m-0 mb-4"
              style="width: 250px"
            >
              Reset
            </button>
            </div>
          </div>
        </form>
        <!--Success Modal -->
        <div>
          <div class="modal fade" id="submissionModal" tabindex="-1" aria-labelledby="submissionModalLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered">
              <div class="modal-content txt-color">
                <div class="modal-header">
                  <h5 class="modal-title" id="submissionModalLabel">Thank you {{ name }}</h5>
                  <button type="button" class="btn-close text-white" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                  <p>We're committed to using your review to improve.</p>
                  <img src="../assets/LazLogo.svg" alt="Bootstrap" width="100" height="100">
                </div>
              </div>
            </div>
          </div>
          <div v-if="errorMessage != ''" class="alert alert-danger mt-2" role="alert">
            {{ errorMessage }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.split-bg {
  background: linear-gradient(to bottom, #0a323d 40%, #ffffff 40%);
}
/* Button style */
.btn-color {
  background-color: #3d8ad0;
}
.btn-text-color {
  color: #ffffff;
}
</style>

<script>
import axios from "axios";
import { Modal } from "bootstrap";



export default {
  data() {
    return {
      content: "",
      phoneNumber: "",
      author: "",
      rating: "",
      successMessage: "",
      errorMessage: "",
      post: {},
      isSubmissionOk: false,
      name: ""
    };
  },
  content: {
    name: "Yohan",
  },
  methods: {
    async createReview() {
      try {
        const { data } = await axios
          .post(
            //"https://localhost:7165/api/Review",
            "https://www.bloggyapi.com/api/Review",
            {
              phoneNumber: this.phoneNumber,
              content: this.content,
              author: this.author,
              email: this.email,
              rating: this.rating,
            }
          )
          .then(
            this.name = this.author,
            this.content = "",
            this.phoneNumber = "",
            this.author = "",
            this.email = "",
            this.rating = "",
            this.isSubmissionOk = true,
            this.author = this.author,
          );
          const modalElement = document.getElementById("submissionModal");
          const submissionModal = new Modal(modalElement);
          if(this.isSubmissionOk) {
            submissionModal.show();
          };
      } catch (error) {
        this.errorMessage = "Failed to submit review. Please try again.";
      }
    },
  },
};
</script>
