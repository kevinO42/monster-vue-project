<template>
  <div class="main">
      <div class="card">
          <div class="card-header"><h5>Create User</h5></div>
          <div class="card-body">
              <form @submit.prevent="handleSubmit" :class="!validated ? 'row g-3 needs-validation' : 'row g-3 was-validated'" novalidate>
                <div class="col-md-4 has-validation">
                    <label for="firstname" class="form-label">First name</label>
                    <input type="text" v-model="form.firstname" class="form-control" id="firstname" placeholder="Enter firstname" required />
                    <div v-if="errors.err_firstname" class="invalid-feedback">
                        {{ errors.err_firstname }}
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="lastname" class="form-label">Last name</label>
                    <input type="text" v-model="form.lastname" class="form-control " id="lastname" placeholder="Enter lastname" required />
                    <div v-if="errors.err_lastname" class="invalid-feedback">
                        {{ errors.err_lastname }}
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="email" class="form-label">Email</label>
                    <input type="email" v-model="form.email" class="form-control" id="email" placeholder="Enter email" required />
                    <div v-if="errors.err_email" class="invalid-feedback">
                        {{ errors.err_email }}
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="birthdate" class="form-label">Date of Birth</label>
                    <input type="date" v-model="form.birthdate" class="form-control" id="birthdate" required />
                    <div v-if="errors.err_birthdate" class="invalid-feedback">
                        {{ errors.err_birthdate }}
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="credit_card" class="form-label">Credit Card</label>
                    <input type="text" v-model="form.credit_card" class="form-control" id="credit_card" placeholder="XXXX-XXXX-XXXX-XXXX" required />
                    <div v-if="errors.err_credit_card" class="invalid-feedback">
                        {{ errors.err_credit_card }}
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="title" class="form-label">Employment Title</label>
                    <input type="text" v-model="form.title" class="form-control" id="title" placeholder="Enter title" required />
                    <div v-if="errors.err_title" class="invalid-feedback">
                        {{ errors.err_title }}
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
                    <div v-if="errors.err_lastname" class="invalid-feedback">
                        {{ errors.err_status }}
                    </div>
                </div>
                <div class="col-md-4">
                    <label for="avatar" class="form-label">Upload Avatar (optional)</label>
                    <input type="file" class="form-control" id="avatar">
                </div>
                <div class="col-12">
                    <button class="btn btn-success" type="submit">Register User</button>
                </div>
              </form>
          </div>
      </div>
  </div>
</template>

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
                avatar: true
            },
            errors: {
                err_firstname: '',
                err_lastname: '',
                err_email: '',
                err_birthdate: '',
                err_credit_card: '',
                err_title: '',
                err_status: '',
                err_avatar: ''
            },
            validated: false
        }
    },

    methods: {
        handleValidation(error) {
            // simple validation for demo purposes only
            this.errors.err_firstname = error.err_firstname.length ? '' : 'This is a required field.'
            this.errors.err_lastname = error.err_lastname.length ? '' : 'This is a required field.'
            this.errors.err_email = error.err_email.length ? '' : 'This is a required field.'
            this.errors.err_birthdate = error.err_birthdate.length ? '' : 'This is a required field.'
            this.errors.err_credit_card = error.err_credit_card.length ? '' : 'This is a required field.'
            this.errors.err_title = error.err_title.length ? '' : 'This is a required field.'
            this.errors.err_status = error.err_status.length ? '' : 'This is a required field.'
        },

        handleSubmit() {
            // check validation process
            this.validated = true

            // execute validation
            this.handleValidation(this.errors)

            // display to console form
            console.log(this.form)
        }
    }
}
</script>