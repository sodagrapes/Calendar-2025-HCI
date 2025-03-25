<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2025 Calendar</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Parisienne&display=swap" rel="stylesheet">
    <style>
        body {
            background-color: #f3e6fa;
            color: #5a3472;
            font-family: 'Parisienne', cursive;
        }
        .calendar-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            padding: 15px;
        }
        .calendar-month {
            background: #fff;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            margin: 15px;
            padding: 20px;
            text-align: center;
            width: 350px;
        }
        table {
            width: 100%;
            margin: 0 auto;
            border-collapse: collapse;
        }
        th, td {
            width: 14.28%; /* Equal column width */
            height: 40px;
            text-align: center;
            border: 1px solid #d8b3ff;
            color: #5a3472;
            font-family: 'Parisienne', cursive;
        }
        th {
            background-color: #d8b3ff;
            color: white;
        }
    </style>
</head>
<body class="container mt-4">
    <h1 class="text-center">2025 Calendar</h1>
    <div class="calendar-container" id="calendar-container">
    </div>
    <script>
        const months = [
            "January", "February", "March", "April", "May", "June",
            "July", "August", "September", "October", "November", "December"
        ];
        const daysInMonth = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];

        function generateCalendar(year) {
            let container = document.getElementById("calendar-container");
            container.innerHTML = "";
            for (let month = 0; month < 12; month++) {
                let firstDay = new Date(year, month, 1).getDay(); // Get starting day (0-6)
                let monthDiv = document.createElement("div");
                monthDiv.classList.add("calendar-month");
                let table = `<h4>${months[month]}</h4>
                             <table class="table table-bordered">
                                <thead>
                                    <tr>
                                        <th>Sun</th><th>Mon</th><th>Tue</th><th>Wed</th>
                                        <th>Thu</th><th>Fri</th><th>Sat</th>
                                    </tr>
                                </thead>
                                <tbody>`;
                let day = 1;
                for (let row = 0; row < 6; row++) {
                    table += "<tr>";
                    for (let col = 0; col < 7; col++) {
                        if (row === 0 && col < firstDay) {
                            table += "<td></td>"; // Empty cells before the first day
                        } else if (day > daysInMonth[month]) {
                            table += "<td></td>"; // Empty cells after last day
                        } else {
                            table += `<td>${day}</td>`;
                            day++;
                        }
                    }
                    table += "</tr>";
                    if (day > daysInMonth[month]) break; // Stop if the month is done
                }
                table += "</tbody></table>";
                monthDiv.innerHTML = table;
                container.appendChild(monthDiv);
            }
        }
        generateCalendar(2025);
    </script>
</body>
</html>

