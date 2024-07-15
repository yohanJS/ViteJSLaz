<template>
  <div class="container-fluid pt-5 pb-5 p-3">
    <div class="row d-flex justify-content-center">
      <div class="col-12 col-md-6">
        <form
          class="border-none shadow-lg rounded-2 p-3"
          id="reviewForm"
          v-on:submit.prevent="createReview"
        >
        <div class="row">
          <div class="col-12 text-start">
            <label class="lead fw-bold mt-2 mb-1">Rate your experience</label>
          </div>
          <div class="col-12 col-md-6 mt-3 text-start">
            <label class="form-label">Full Name</label>
            <input
              required
              class="form-control"
              for="author"
              aria-label="Enter author's name"
              v-model="author"
            />
          </div>
          <div class="col-12 col-md-6 mt-3 text-start">
            <label class="form-label">Phone Number</label>
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
            <label class="form-label">Email</label>
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
          <label class="form-label">Write a review</label>
          <textarea required
            class="form-control"
            for="content"
            aria-label="Write a summary of your service"
            v-model="content"
            rows="3"
            cols="50"
          ></textarea>
        </div>
          <div class="col-12 mt-3">
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
          <div class="row text-end pb-4">
          <div class="col-12 text-center">
            <button
              type="reset"
              id="reset"
              class="btn btn-outline-danger fw-bold mt-5 me-1"
              style="width: 120px"
            >
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-eraser" viewBox="0 0 16 16">
              <path d="M8.086 2.207a2 2 0 0 1 2.828 0l3.879 3.879a2 2 0 0 1 0 2.828l-5.5 5.5A2 2 0 0 1 7.879 15H5.12a2 2 0 0 1-1.414-.586l-2.5-2.5a2 2 0 0 1 0-2.828zm2.121.707a1 1 0 0 0-1.414 0L4.16 7.547l5.293 5.293 4.633-4.633a1 1 0 0 0 0-1.414zM8.746 13.547 3.453 8.254 1.914 9.793a1 1 0 0 0 0 1.414l2.5 2.5a1 1 0 0 0 .707.293H7.88a1 1 0 0 0 .707-.293z"/>
            </svg>
              Reset
            </button>
            <button
              type="submit"
              id="submit"
              class="btn btn-color btn-text-color fw-bold mt-5"
              style="width: 120px"
            >
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-send" viewBox="0 0 16 16">
              <path d="M15.854.146a.5.5 0 0 1 .11.54l-5.819 14.547a.75.75 0 0 1-1.329.124l-3.178-4.995L.643 7.184a.75.75 0 0 1 .124-1.33L15.314.037a.5.5 0 0 1 .54.11ZM6.636 10.07l2.761 4.338L14.13 2.576zm6.787-8.201L1.591 6.602l4.339 2.76z"/>
            </svg>
              Submit
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

          setTimeout(function(){
            window.location.reload();
            window.location.href = "#reviews";
          }, 5000);

      } catch (error) {
        this.errorMessage = "Failed to submit review. Please try again.";
      }
    },
  },
};
</script>
