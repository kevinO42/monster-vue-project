<template>
  <div class="main">
      <div class="card">
          <div class="card-header"><h5>Create User</h5></div>
          <div class="card-body">
              <form @submit.prevent="handleSubmit" :class="!is_validated ? 'row g-3 needs-validation' : 'row g-3 was-validated'" novalidate>
                <div class="col-md-4 has-validation">
                    <label for="firstname" class="form-label">First name</label>
                    <input type="text" v-model="form.firstname" class="form-control" id="firstname" placeholder="Enter firstname" required />
                    <div class="invalid-feedback">
                        This is a required field.
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="lastname" class="form-label">Last name</label>
                    <input type="text" v-model="form.lastname" class="form-control " id="lastname" placeholder="Enter lastname" required />
                    <div class="invalid-feedback">
                        This is a required field.
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="email" class="form-label">Email</label>
                    <input type="email" v-model="form.email" class="form-control" id="email" placeholder="Enter email" required />
                    <div class="invalid-feedback">
                         This is a required field.
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="birthdate" class="form-label">Date of Birth</label>
                    <input type="date" v-model="form.birthdate" class="form-control" id="birthdate" required />
                    <div class="invalid-feedback">
                         This is a required field.
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="credit_card" class="form-label">Credit Card</label>
                    <input type="text" v-model="form.credit_card" class="form-control" id="credit_card" placeholder="XXXX-XXXX-XXXX-XXXX" required />
                    <div class="invalid-feedback">
                        This is a required field.
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="title" class="form-label">Employment Title</label>
                    <input type="text" v-model="form.title" class="form-control" id="title" placeholder="Enter title" required />
                    <div class="invalid-feedback">
                        This is a required field.
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="status" class="form-label">Subscription</label>
                    <select v-model="form.status" class="form-select" id="status" required>
                        <option value="Active">Active</option>
                        <option value="Idle">Idle</option>
                        <option value="Pending">Pending</option>
                        <option value="Blocked">Blocked</option>
                    </select>
                    <div class="invalid-feedback">
                        This is a required field.
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="avatar" class="form-label">Upload Avatar (optional)</label>
                    <input type="file" @change="handleUpload($event)" class="form-control" id="avatar">
                </div>
                <div class="col-12">
                    <button class="btn btn-success" type="submit">Register User</button>
                </div>
              </form>
          </div>
      </div>
  </div>
</template>
import axios from 
<script>

export default {
    data() {
        return {
            form: {
                firstname: '',
                lastname: '',
                email: '',
                birthdate: '',
                credit_card: '',
                title: '',
                status: '',
                avatar: ''
            },
            errors: [],
            is_validated: false,
            has_passed:false

        }
    },

    methods: {
        handleValidation() {
            this.errors.splice(0)
            this.errors.push(this.form.firstname.length > 0 ? true : false)
            this.errors.push(this.form.lastname.length > 0 ? true : false)
            this.errors.push(this.form.email.length > 0 ? true : false)
            this.errors.push(this.form.birthdate.length > 0 ? true : false)
            this.errors.push(this.form.credit_card.length > 0 ? true : false)
            this.errors.push(this.form.title.length > 0 ? true : false)
            this.errors.push(this.form.status.length > 0 ? true : false)

            // check for errors
            this.has_passed = this.errors.indexOf(false) == -1 ? true : false
        },

        handleUpload(event) {
            this.form.avatar = event.target.files[0];
        },

        handleSubmit() {
            // trigger bootstrap validation process
            this.is_validated = true

            // execute validation
            this.handleValidation()

            // if no more errors send post request
            if (this.has_passed) {
                // POST request using fetch with error handling
                let post = JSON.stringify({
                    first_name: this.form.firstname,
                    last_name: this.form.lastname,
                    email: this.form.email,
                    credit_card: this.form.credit_card,
                    title: this.form.title,
                    status: this.form.status,
                    avatar: this.form.avatar
                })

                const requestSettings = {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: post
                };

                // display form submission to console
                console.log(post)

                // doesn't work due to dummy URL
                fetch('http://localhost:8080/registration/post', requestSettings)
                    .then(async response => {
                        const data = await response.json();
                    })
                    .catch(error => {
                        this.errorMessage = error;
                        console.error('There was an error!', error);
                    });
            }  
        }
    }
}
</script>