# Company Input Validations

A central, enterprise-grade validation library for all internal company projects. This repository ensures that every app (web, mobile, and backend) uses the exact same strict security rules for user input.

## 📦 Installation

Since this is a private company repository, you can install it directly from GitHub using NPM:

    npm install git+https://github.com/Organization-wide-Standards/Input-Validations.git

## 🚀 Available Validations

We have 18 highly secure validators ready to use. Every validator returns a `ValidationResult` object containing `isValid` (boolean) and an `errorMessage` (string | null) so you can easily show errors in your UI.

**Identity & Auth:**
* `validateEmail`, `validatePassword`, `validateUsername`
* `validateFirstName`, `validateLastName`, `validateFullName`
* `validateDateOfBirth`, `validatePhoneNumber`

**Location & Business:**
* `validateAddress`, `validatePostalCode`
* `validateCompanyName`, `validateUrl`

**Financial & Secure IDs:**
* `validateAccountNumber`, `validateIFSCCode`, `validateBankName`
* `validatePanCard`, `validateAadhaar`, `validateCurrency`

## 💻 How to Use (Example)

Here is a quick example of how to use this library inside a React or React Native component:

```tsx
import React, { useState } from 'react';
import { validateEmail, validatePassword } from 'input-validations';

const LoginScreen = () => {
  const [email, setEmail] = useState('');
  const [error, setError] = useState<string | null>(null);

  const handleLogin = () => {
    // 1. Run the validator
    const emailCheck = validateEmail(email);

    // 2. Check the result
    if (!emailCheck.isValid) {
      // 3. Display the exact error message to the user!
      setError(emailCheck.errorMessage);
      return;
    }

    // Success! Safe to send to backend.
  };

  return (
    <div>
      <input 
        placeholder="Enter Email" 
        value={email} 
        onChange={(e) => setEmail(e.target.value)} 
      />
      {error && <p style={{ color: 'red' }}>{error}</p>}
      
      <button onClick={handleLogin}>Login</button>
    </div>
  );
};
