+++
title = "Randomizer (general)"
author = ["Aidin Biibosunov"]
lastmod = 2026-02-28T07:24:57+01:00
tags = ["teaching", "tools"]
categories = ["teaching"]
draft = false
type = "teaching"
+++

<textarea id="studentsInput" placeholder="Enter student names, one per line" rows="10" cols="50"></textarea><br><br>
<input type="number" id="numberInput" placeholder="Enter the number of selections" min="1">
<button onclick="selectRandomStudent()">Select Random Student</button>
<button onclick="resetSelection()">Reset Selection</button>

<div id="latestOutput" style="margin-top: 20px; font-weight: bold;"></div>
<div id="selectedStudentsOutput" style="margin-top: 10px; font-weight: bold;"></div>

<script>
let selectedStudents = [];
let availableStudents = [];

function getRandomStudent() {
    if (availableStudents.length === 0) {
        return null; // No more students available
    }
    const randomIndex = Math.floor(Math.random() * availableStudents.length);
    return availableStudents.splice(randomIndex, 1)[0]; // Remove and return the selected student
}

function selectRandomStudent() {
    const N = parseInt(document.getElementById('numberInput').value, 10);
    const studentsInput = document.getElementById('studentsInput').value.trim();

    if (!studentsInput) {
        document.getElementById('latestOutput').innerText = "Please enter a list of students.";
        return;
    }

    if (isNaN(N) || N < 1) {
        document.getElementById('latestOutput').innerText = "Please enter a valid number greater than 0.";
        return;
    }

    if (selectedStudents.length === 0) {
        // Split the input by new lines and trim any extra spaces
        availableStudents = studentsInput.split('\n').map(student => student.trim()).filter(student => student.length > 0);
        if (availableStudents.length === 0) {
            document.getElementById('latestOutput').innerText = "Please enter at least one student name.";
            return;
        }
        selectedStudents = []; // Reset selected students list
    }

    let outputText = '';
    for (let i = 0; i < N; i++) {
        const randomStudent = getRandomStudent();
        if (randomStudent !== null) {
            selectedStudents.push(randomStudent);
        } else {
            document.getElementById('latestOutput').innerText = "All students have been selected.";
            break;
        }
    }

    // Update the output to reflect all selected students, adding <br> after every N selections
    outputText = selectedStudents.map((student, index) => {
        return student + ((index + 1) % N === 0 ? '<br>' : ', ');
    }).join('');

    document.getElementById('selectedStudentsOutput').innerHTML = "Selected students:<br>" + outputText;
}

function resetSelection() {
    document.getElementById('latestOutput').innerText = "Selection reset. You can start over.";
    document.getElementById('selectedStudentsOutput').innerHTML = ""; // Clear selected students output
    selectedStudents = [];
    availableStudents = [];
}
</script>

-   [Recommendations](/html_files/recommendations.html)
