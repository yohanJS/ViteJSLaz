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
            <label class="form-label fw-bold">Rate your experience</label>
            <br />
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-5-circle-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0m-8.006 4.158c1.74 0 2.924-1.119 2.924-2.806 0-1.641-1.178-2.584-2.56-2.584-.897 0-1.442.421-1.612.68h-.064l.193-2.344h3.621V4.002H5.791L5.445 8.63h1.149c.193-.358.668-.809 1.435-.809.85 0 1.582.604 1.582 1.57 0 1.085-.779 1.682-1.57 1.682-.697 0-1.389-.31-1.53-1.031H5.276c.065 1.213 1.149 2.115 2.72 2.115Z"
              />
            </svg>
            ★★★★★
            <input
              required
              class="form-check-input"
              aria-label="Rate your service"
              for="rating"
              v-model="rating"
              type="radio"
              id="star5"
              name="rating"
              value="5"
            />
            <br />
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-4-circle-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0M7.519 5.057c-.886 1.418-1.772 2.838-2.542 4.265v1.12H8.85V12h1.26v-1.559h1.007V9.334H10.11V4.002H8.176zM6.225 9.281v.053H8.85V5.063h-.065c-.867 1.33-1.787 2.806-2.56 4.218"
              />
            </svg>
            ★★★★
            <input
              required
              class="form-check-input"
              aria-label="Rate your service"
              for="rating"
              v-model="rating"
              type="radio"
              id="star4"
              name="rating"
              value="4"
            />
            <br />
            <svg
              xmlns="http://www.w3.org/2000/svg"
              for="rating"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-3-circle-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0m-8.082.414c.92 0 1.535.54 1.541 1.318.012.791-.615 1.36-1.588 1.354-.861-.006-1.482-.469-1.54-1.066H5.104c.047 1.177 1.05 2.144 2.754 2.144 1.653 0 2.954-.937 2.93-2.396-.023-1.278-1.031-1.846-1.734-1.916v-.07c.597-.1 1.505-.739 1.482-1.876-.03-1.177-1.043-2.074-2.637-2.062-1.675.006-2.59.984-2.625 2.12h1.248c.036-.556.557-1.054 1.348-1.054.785 0 1.348.486 1.348 1.195.006.715-.563 1.237-1.342 1.237h-.838v1.072h.879Z"
              />
            </svg>
            ★★★
            <input
              required
              class="form-check-input"
              aria-label="Rate your service"
              for="rating"
              v-model="rating"
              type="radio"
              id="star3"
              name="rating"
              value="3"
            />
            <br />
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-2-circle-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0M6.646 6.24c0-.691.493-1.306 1.336-1.306.756 0 1.313.492 1.313 1.236 0 .697-.469 1.23-.902 1.705l-2.971 3.293V12h5.344v-1.107H7.268v-.077l1.974-2.22.096-.107c.688-.763 1.287-1.428 1.287-2.43 0-1.266-1.031-2.215-2.613-2.215-1.758 0-2.637 1.19-2.637 2.402v.065h1.271v-.07Z"
              />
            </svg>
            ★★
            <input
              required
              class="form-check-input"
              aria-label="Rate your service"
              for="rating"
              v-model="rating"
              type="radio"
              id="star2"
              name="rating"
              value="2"
            />
            <br />
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-1-circle-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0M9.283 4.002H7.971L6.072 5.385v1.271l1.834-1.318h.065V12h1.312z"
              />
            </svg>
            ★
            <input
              required
              class="form-check-input"
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
