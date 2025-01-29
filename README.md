<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Registration</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <section class="container">
        <h1>Tech Conference Registration</h1>
        <form id="registrationForm" novalidate>
            <label for="fullName">Full Name:</label>
            <input type="text" id="fullName" placeholder="Enter your full name" required autofocus>

            <label for="email">Email Address:</label>
            <input type="email" id="email" required>

            <label for="contactNumber">Contact Number:</label>
            <input type="tel" id="contactNumber" pattern="^\(\d{3}\) \d{3}-\d{4}$" required placeholder="(XXX) XXX-XXXX">

            <label for="website">Website or Portfolio:</label>
            <input type="url" id="website">

            <label for="interests">Event Interests:</label>
            <input type="text" id="interests" list="interestOptions" required>
            <datalist id="interestOptions">
                <option value="Web Development">
                <option value="AI">
                <option value="Cloud Computing">
                <option value="Cybersecurity">
                <option value="Data Science">
            </datalist>

            <label for="resume">Upload Resume:</label>
            <input type="file" id="resume" multiple>

            <label for="sessionPreferences">Select Session Preferences:</label>
            <select id="sessionPreferences">
                <option value="standard">Standard Session</option>
                <option value="vip" disabled>VIP Session</option>
                <option value="workshop">Workshop</option>
            </select>

            <fieldset>
                <legend>Profile Type:</legend>
                <label><input type="radio" name="profileType" value="student" required> Student</label>
                <label><input type="radio" name="profileType" value="professional"> Professional</label>
                <label><input type="radio" name="profileType" value="speaker"> Speaker</label>
            </fieldset>

            <div id="speakerFields" style="display: none;">
                <label for="topic">Topic of Presentation:</label>
                <input type="text" id="topic" placeholder="Enter your presentation topic">
            </div>

            <fieldset>
                <legend>Workshop Preferences:</legend>
                <label><input type="checkbox" name="workshops" value="workshop1"> Workshop 1</label>
                <label><input type="checkbox" name="workshops" value="workshop2"> Workshop 2</label>
                <label><input type="checkbox" name="workshops" value="workshop3"> Workshop 3</label>
            </fieldset>

            <label for="notes">Additional Notes:</label>
            <textarea id="notes" placeholder="Enter any dietary restrictions." readonly></textarea>

            <button type="submit">Submit</button>
            <button type="reset">Reset</button>
        </form>
    </section>
    <script src="script.js"></script>
</body>
</html>



body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 600px;
    margin: auto;
    background: white;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
}

label {
    display: block;
    margin: 10px 0 5px;
}

input, select, textarea {
    width: 100%;
    padding: 10px;
    margin-bottom: 20px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

input:invalid {
    border-color: red;
}

button {
    padding: 10px 15px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button[type="reset"] {
    background-color: #dc3545;
}

button:hover {
    opacity: 0.8;
}

#speakerFields {
    margin-top: 20px;
}

fieldset {
    border: 1px solid #ccc;
    padding: 10px;
    margin-bottom: 20px;
}

legend {
    font-weight: bold;
}

@media (max-width: 600px) {
    .container {
        padding: 15px;
    }

    button {
        width: 100%;
        margin-top: 10px;
    }
}




document.addEventListener('DOMContentLoaded', function() {
    const profileTypeRadios = document.querySelectorAll('input[name="profileType"]');
    const speakerFields = document.getElementById('speakerFields');

    profileTypeRadios.forEach(radio => {
        radio.addEventListener('change', function() {
            if (this.value === 'speaker') {
                speakerFields.style.display = 'block';
            } else {
                speakerFields.style.display = 'none';
            }
        });
    });

    const form = document.getElementById('registrationForm');
    form.addEventListener('submit', function(event) {
        if (!form.checkValidity()) {
            event.preventDefault();
            alert('Please fill out all required fields correctly.');
        }
    });
});
