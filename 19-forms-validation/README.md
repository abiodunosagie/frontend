# 19 - Forms & Validation

> **"Forms are how users talk to your app. Make the conversation smooth."**

Forms are everywhere - login, signup, checkout, contact, search. Mastering forms is essential.

---

## 🎯 What You'll Master

By the end of this module, you'll:
- **Build** accessible, user-friendly forms
- **Validate** user input (client-side and best practices)
- **Handle** form submission in React/Next.js
- **Use** React Hook Form (professional approach)
- **Provide** great error messages and UX

---

## 📚 Lessons

### Week 1: HTML Forms Mastery
1. **[Form Basics](./lessons/01-form-basics.md)** - Inputs, labels, buttons
2. **[Input Types](./lessons/02-input-types.md)** - text, email, password, number, etc.
3. **[HTML5 Validation](./lessons/03-html5-validation.md)** - required, pattern, min, max
4. **[Form Accessibility](./lessons/04-form-accessibility.md)** - Labels, ARIA, errors

### Week 2: JavaScript Validation
5. **[JavaScript Validation](./lessons/05-js-validation.md)** - Custom validation logic
6. **[Error Handling](./lessons/06-error-handling.md)** - Displaying errors properly
7. **[Form Submission](./lessons/07-form-submission.md)** - Handling submit events

### Week 3: React Forms
8. **[Controlled Components](./lessons/08-controlled-components.md)** - React form pattern
9. **[Form State Management](./lessons/09-form-state.md)** - Managing complex forms
10. **[React Hook Form](./lessons/10-react-hook-form.md)** - Professional library

---

## 🎨 Form Example (HTML + Validation)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Contact Form</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      padding: 40px;
      background: #f5f5f5;
    }

    form {
      max-width: 500px;
      margin: 0 auto;
      background: white;
      padding: 30px;
      border-radius: 8px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }

    h1 {
      margin-bottom: 20px;
    }

    .form-group {
      margin-bottom: 20px;
    }

    label {
      display: block;
      margin-bottom: 5px;
      font-weight: bold;
      color: #333;
    }

    input,
    textarea {
      width: 100%;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 4px;
      font-size: 16px;
    }

    input:focus,
    textarea:focus {
      outline: none;
      border-color: #007bff;
      box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.1);
    }

    input.error,
    textarea.error {
      border-color: #dc3545;
    }

    .error-message {
      color: #dc3545;
      font-size: 14px;
      margin-top: 5px;
      display: none;
    }

    .error-message.show {
      display: block;
    }

    button {
      width: 100%;
      padding: 12px;
      background: #007bff;
      color: white;
      border: none;
      border-radius: 4px;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover {
      background: #0056b3;
    }

    button:disabled {
      background: #ccc;
      cursor: not-allowed;
    }

    .success-message {
      background: #d4edda;
      color: #155724;
      padding: 15px;
      border-radius: 4px;
      margin-bottom: 20px;
      display: none;
    }

    .success-message.show {
      display: block;
    }
  </style>
</head>
<body>
  <form id="contactForm" novalidate>
    <h1>Contact Us</h1>

    <div class="success-message" id="successMessage">
      Thank you! Your message has been sent.
    </div>

    <div class="form-group">
      <label for="name">Name *</label>
      <input
        type="text"
        id="name"
        name="name"
        required
        minlength="2"
        maxlength="50"
      >
      <div class="error-message" id="nameError"></div>
    </div>

    <div class="form-group">
      <label for="email">Email *</label>
      <input
        type="email"
        id="email"
        name="email"
        required
      >
      <div class="error-message" id="emailError"></div>
    </div>

    <div class="form-group">
      <label for="phone">Phone</label>
      <input
        type="tel"
        id="phone"
        name="phone"
        pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}"
        placeholder="123-456-7890"
      >
      <div class="error-message" id="phoneError"></div>
    </div>

    <div class="form-group">
      <label for="message">Message *</label>
      <textarea
        id="message"
        name="message"
        rows="5"
        required
        minlength="10"
        maxlength="500"
      ></textarea>
      <div class="error-message" id="messageError"></div>
    </div>

    <button type="submit">Send Message</button>
  </form>

  <script>
    const form = document.getElementById('contactForm');
    const successMessage = document.getElementById('successMessage');

    // Form inputs
    const nameInput = document.getElementById('name');
    const emailInput = document.getElementById('email');
    const phoneInput = document.getElementById('phone');
    const messageInput = document.getElementById('message');

    // Error elements
    const nameError = document.getElementById('nameError');
    const emailError = document.getElementById('emailError');
    const phoneError = document.getElementById('phoneError');
    const messageError = document.getElementById('messageError');

    // Validation functions
    function validateName() {
      const value = nameInput.value.trim();

      if (value === '') {
        showError(nameInput, nameError, 'Name is required');
        return false;
      }

      if (value.length < 2) {
        showError(nameInput, nameError, 'Name must be at least 2 characters');
        return false;
      }

      clearError(nameInput, nameError);
      return true;
    }

    function validateEmail() {
      const value = emailInput.value.trim();

      if (value === '') {
        showError(emailInput, emailError, 'Email is required');
        return false;
      }

      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailRegex.test(value)) {
        showError(emailInput, emailError, 'Please enter a valid email');
        return false;
      }

      clearError(emailInput, emailError);
      return true;
    }

    function validatePhone() {
      const value = phoneInput.value.trim();

      // Phone is optional, so if empty, it's valid
      if (value === '') {
        clearError(phoneInput, phoneError);
        return true;
      }

      const phoneRegex = /^[0-9]{3}-[0-9]{3}-[0-9]{4}$/;
      if (!phoneRegex.test(value)) {
        showError(phoneInput, phoneError, 'Format: 123-456-7890');
        return false;
      }

      clearError(phoneInput, phoneError);
      return true;
    }

    function validateMessage() {
      const value = messageInput.value.trim();

      if (value === '') {
        showError(messageInput, messageError, 'Message is required');
        return false;
      }

      if (value.length < 10) {
        showError(messageInput, messageError, 'Message must be at least 10 characters');
        return false;
      }

      clearError(messageInput, messageError);
      return true;
    }

    function showError(input, errorElement, message) {
      input.classList.add('error');
      errorElement.textContent = message;
      errorElement.classList.add('show');
    }

    function clearError(input, errorElement) {
      input.classList.remove('error');
      errorElement.textContent = '';
      errorElement.classList.remove('show');
    }

    // Real-time validation
    nameInput.addEventListener('blur', validateName);
    emailInput.addEventListener('blur', validateEmail);
    phoneInput.addEventListener('blur', validatePhone);
    messageInput.addEventListener('blur', validateMessage);

    // Form submission
    form.addEventListener('submit', function(e) {
      e.preventDefault();

      // Validate all fields
      const isNameValid = validateName();
      const isEmailValid = validateEmail();
      const isPhoneValid = validatePhone();
      const isMessageValid = validateMessage();

      // If all valid, submit
      if (isNameValid && isEmailValid && isPhoneValid && isMessageValid) {
        // Show success message
        successMessage.classList.add('show');

        // Reset form
        form.reset();

        // Hide success message after 5 seconds
        setTimeout(() => {
          successMessage.classList.remove('show');
        }, 5000);

        // In real app, you'd send data to server here
        console.log('Form submitted!');
      }
    });
  </script>
</body>
</html>
```

**This is a production-ready form with:**
- Proper validation
- Error messages
- Accessibility
- User feedback
- Real-time validation

---

## 🎯 React Form Example (Controlled Components)

```javascript
'use client';

import { useState } from 'react';

export default function ContactForm() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    message: ''
  });

  const [errors, setErrors] = useState({});
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [success, setSuccess] = useState(false);

  function handleChange(e) {
    const { name, value } = e.target;
    setFormData(prev => ({
      ...prev,
      [name]: value
    }));

    // Clear error when user starts typing
    if (errors[name]) {
      setErrors(prev => ({
        ...prev,
        [name]: ''
      }));
    }
  }

  function validate() {
    const newErrors = {};

    if (!formData.name.trim()) {
      newErrors.name = 'Name is required';
    } else if (formData.name.trim().length < 2) {
      newErrors.name = 'Name must be at least 2 characters';
    }

    if (!formData.email.trim()) {
      newErrors.email = 'Email is required';
    } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.email)) {
      newErrors.email = 'Please enter a valid email';
    }

    if (!formData.message.trim()) {
      newErrors.message = 'Message is required';
    } else if (formData.message.trim().length < 10) {
      newErrors.message = 'Message must be at least 10 characters';
    }

    return newErrors;
  }

  async function handleSubmit(e) {
    e.preventDefault();

    const newErrors = validate();

    if (Object.keys(newErrors).length > 0) {
      setErrors(newErrors);
      return;
    }

    setIsSubmitting(true);

    try {
      // Send to API
      const response = await fetch('/api/contact', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(formData)
      });

      if (!response.ok) {
        throw new Error('Failed to send message');
      }

      setSuccess(true);
      setFormData({ name: '', email: '', message: '' });

      setTimeout(() => setSuccess(false), 5000);

    } catch (error) {
      setErrors({ submit: 'Failed to send message. Please try again.' });
    } finally {
      setIsSubmitting(false);
    }
  }

  return (
    <form onSubmit={handleSubmit} className="max-w-md mx-auto p-6">
      <h1 className="text-2xl font-bold mb-6">Contact Us</h1>

      {success && (
        <div className="bg-green-100 text-green-700 p-4 rounded mb-4">
          Thank you! Your message has been sent.
        </div>
      )}

      {errors.submit && (
        <div className="bg-red-100 text-red-700 p-4 rounded mb-4">
          {errors.submit}
        </div>
      )}

      <div className="mb-4">
        <label htmlFor="name" className="block font-bold mb-2">
          Name *
        </label>
        <input
          type="text"
          id="name"
          name="name"
          value={formData.name}
          onChange={handleChange}
          className={`w-full p-2 border rounded ${
            errors.name ? 'border-red-500' : 'border-gray-300'
          }`}
        />
        {errors.name && (
          <p className="text-red-500 text-sm mt-1">{errors.name}</p>
        )}
      </div>

      <div className="mb-4">
        <label htmlFor="email" className="block font-bold mb-2">
          Email *
        </label>
        <input
          type="email"
          id="email"
          name="email"
          value={formData.email}
          onChange={handleChange}
          className={`w-full p-2 border rounded ${
            errors.email ? 'border-red-500' : 'border-gray-300'
          }`}
        />
        {errors.email && (
          <p className="text-red-500 text-sm mt-1">{errors.email}</p>
        )}
      </div>

      <div className="mb-4">
        <label htmlFor="message" className="block font-bold mb-2">
          Message *
        </label>
        <textarea
          id="message"
          name="message"
          value={formData.message}
          onChange={handleChange}
          rows="5"
          className={`w-full p-2 border rounded ${
            errors.message ? 'border-red-500' : 'border-gray-300'
          }`}
        />
        {errors.message && (
          <p className="text-red-500 text-sm mt-1">{errors.message}</p>
        )}
      </div>

      <button
        type="submit"
        disabled={isSubmitting}
        className="w-full bg-blue-500 text-white p-3 rounded hover:bg-blue-600 disabled:bg-gray-400"
      >
        {isSubmitting ? 'Sending...' : 'Send Message'}
      </button>
    </form>
  );
}
```

---

## 🎯 Key Concepts

### 1. **Controlled vs Uncontrolled**

```javascript
// Controlled (React manages state)
const [value, setValue] = useState('');
<input value={value} onChange={(e) => setValue(e.target.value)} />

// Uncontrolled (DOM manages state)
const inputRef = useRef();
<input ref={inputRef} />
// Access with: inputRef.current.value
```

**Use controlled components in React!**

### 2. **Validation Timing**

- **On submit** - Basic approach
- **On blur** - Validate when user leaves field (better UX)
- **On change** - Real-time feedback (can be annoying)

**Best: Validate on blur, show errors on submit.**

### 3. **Error Messages**

```javascript
// Bad
"Invalid input"

// Good
"Email must include @ symbol"
"Password must be at least 8 characters"
"Please enter a valid phone number (123-456-7890)"
```

**Be specific and helpful!**

---

## 🎯 Projects You'll Build

1. **Login/Signup Form** - Email, password validation
2. **Multi-step Form** - Wizard-style form
3. **Dynamic Form** - Add/remove fields
4. **File Upload Form** - With preview
5. **Search Form** - With autocomplete

---

**Forms are how users interact with your app. Make them great.** ✨
