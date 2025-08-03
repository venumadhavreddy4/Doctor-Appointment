<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Doctor Appointment Booking</title>
    <style>
        * {
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            margin: 0;
            padding: 0;
            background: #f2f2f2;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .container {
            background: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
            max-width: 500px;
            width: 100%;
        }

        h2 {
            text-align: center;
            color: #333;
        }

        label {
            display: block;
            margin-top: 1rem;
            font-weight: bold;
        }

        input,
        select,
        textarea {
            width: 100%;
            padding: 10px;
            margin-top: 0.5rem;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        button {
            width: 100%;
            padding: 12px;
            margin-top: 1.5rem;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }

        button:hover {
            background-color: #45a049;
        }

        .confirmation {
            margin-top: 1rem;
            padding: 1rem;
            background: #d4edda;
            color: #155724;
            border-radius: 5px;
            display: none;
        }
    </style>
</head>

<body>
    <div class="container">
        <h2>Book an Appointment</h2>
        <form id="appointmentForm">
            <label for="name">Full Name:</label>
            <input type="text" id="name" required />

            <label for="email">Email:</label>
            <input type="email" id="email" required />

            <label for="doctor">Select Doctor:</label>
            <select id="doctor" required>
                <option value="">-- Select --</option>
                <option value="Dr. Smith">Dr. Smith - Cardiologist</option>
                <option value="Dr. Kumar">Dr. Kumar - Dermatologist</option>
                <option value="Dr. Rao">Dr. Rao - Neurologist</option>
            </select>

            <label for="date">Appointment Date:</label>
            <input type="date" id="date" required />

            <label for="notes">Additional Notes:</label>
            <textarea id="notes" rows="3"></textarea>

            <button type="submit">Book Appointment</button>
        </form>

        <div class="confirmation" id="confirmationMessage"></div>
    </div>

    <script>
        const form = document.getElementById("appointmentForm");
        const confirmationMessage = document.getElementById("confirmationMessage");

        form.addEventListener("submit", function(event) {
            event.preventDefault();

            const name = document.getElementById("name").value;
            const email = document.getElementById("email").value;
            const doctor = document.getElementById("doctor").value;
            const date = document.getElementById("date").value;

            if (!name || !email || !doctor || !date) {
                alert("Please fill in all required fields.");
                return;
            }

            confirmationMessage.innerHTML = `
        <strong>Appointment Confirmed!</strong><br>
        Thank you, ${name}. Your appointment with <strong>${doctor}</strong> on <strong>${date}</strong> is booked.
      `;
            confirmationMessage.style.display = "block";
            form.reset();
        });
    </script>
</body>

</html>
