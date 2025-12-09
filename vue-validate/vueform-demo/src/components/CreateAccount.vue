<template>
  <div class="form-card">
    <h2>Create Account</h2>

    <Form @submit="onSubmit" v-slot="{ errors, isSubmitting }">
      <!-- Full Name -->
      <div class="field">
        <label>Full Name *</label>
        <Field
          name="name"
          type="text"
          rules="required|min:3"
          placeholder="John Doe"
          class="input"
        />
        <ErrorMessage name="name" class="error" />
      </div>

      <!-- Email -->
      <div class="field">
        <label>Email *</label>
        <Field
          name="email"
          type="email"
          rules="required|email"
          placeholder="you@example.com"
          class="input"
        />
        <ErrorMessage name="email" class="error" />
      </div>

      <!-- Password -->
      <div class="field">
        <label>Password *</label>
        <Field
          name="password"
          type="password"
          rules="required|min:8"
          placeholder="••••••••"
          class="input"
        />
        <ErrorMessage name="password" class="error" />
      </div>

      <!-- Terms -->
      <div class="checkbox-field">
        <Field
          name="terms"
          type="checkbox"
          value="true"
          rules="required"
          class="checkbox"
        />
        <label class="checkbox-label">
          I agree to Terms & Conditions *
        </label>
      </div>
      <ErrorMessage name="terms" class="error" />

      <!-- Submit -->
      <button
        type="submit"
        :disabled="isSubmitting || Object.keys(errors).length > 0"
        class="submit-btn"
      >
        {{ isSubmitting ? 'Creating...' : 'Create Account' }}
      </button>
    </Form>
  </div>
</template>

<script>
import { Form, Field, ErrorMessage, defineRule } from 'vee-validate'
import { required, email, min } from '@vee-validate/rules'

// Szabályok regisztrálása
defineRule('required', required)
defineRule('email', email)
defineRule('min', min)

export default {
  components: { Form, Field, ErrorMessage },
  methods: {
    onSubmit(values) {
      console.log('Sikeres regisztráció:', values)
      alert('Account created successfully! 🎉')
    }
  }
}
</script>

<style scoped>
.form-card {
  background: white;
  padding: 32px 40px;
  border-radius: 16px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
  font-family: system-ui, -apple-system, sans-serif;
}

h2 {
  text-align: center;
  margin: 0 0 24px 0;
  font-size: 28px;
  color: #111827;
  font-weight: 700;
}

.field {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 8px;
  font-weight: 600;
  color: #374151;
  font-size: 14px;
}

.input {
  width: 100%;
  padding: 12px 16px;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  font-size: 15px;
  transition: all 0.2s;
}

.input:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

.checkbox-field {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 20px;
  font-size: 14px;
  color: #374151;
}

.checkbox {
  width: 18px;
  height: 18px;
  accent-color: #3b82f6;
}

.checkbox-label {
  cursor: pointer;
  user-select: none;
}

.submit-btn {
  width: 100%;
  padding: 14px;
  background: #3b82f6;
  color: white;
  border: none;
  border-radius: 12px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
  box-shadow: 0 10px 20px rgba(59, 130, 246, 0.25);
}

.submit-btn:hover:not(:disabled) {
  background: #2563eb;
  transform: translateY(-2px);
}

.submit-btn:disabled {
  background: #9ca3af;
  cursor: not-allowed;
  transform: none;
  box-shadow: none;
}

.error {
  color: #ef4444;
  font-size: 13px;
  margin-top: 6px;
  display: block;
}
</style>