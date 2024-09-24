+++
title = "Randomizer"
author = ["Aidin Biibosunov"]
lastmod = 2024-09-24T17:36:15+02:00
tags = ["teaching", "tools"]
categories = ["teaching"]
draft = false
type = "teaching"
+++

<input type="number" id="numberInput" placeholder="Enter N" min="1">
<button onclick="selectRandomNumber()">Select Random Number</button>
<button onclick="resetSelection()">Reset Selection</button>

<div id="latestOutput" style="margin-top: 20px; font-weight: bold;"></div>
<div id="selectedNumbersOutput" style="margin-top: 10px; font-weight: bold;"></div>

<script>
let selectedNumbers = [];
let availableNumbers = [];

function initializeNumbers(N) {
    availableNumbers = Array.from({length: N}, (_, i) => i + 1); // Create array [1, 2, ..., N]
    selectedNumbers = []; // Reset selected numbers
}

function getRandomInteger() {
    if (availableNumbers.length === 0) {
        return null; // No more numbers available
    }
    const randomIndex = Math.floor(Math.random() * availableNumbers.length);
    return availableNumbers.splice(randomIndex, 1)[0]; // Remove and return the selected number
}

function selectRandomNumber() {
    const N = parseInt(document.getElementById('numberInput').value, 10);

    if (isNaN(N) || N < 1) {
        document.getElementById('latestOutput').innerText = "Please enter a valid integer greater than 0.";
        return;
    }

    if (selectedNumbers.length === 0) {
        initializeNumbers(N); // Initialize numbers when N is valid
    }

    const randomNumber = getRandomInteger();
    if (randomNumber !== null) {
        selectedNumbers.push(randomNumber);
        document.getElementById('latestOutput').innerText = "Randomly selected number: " + randomNumber;
        document.getElementById('selectedNumbersOutput').innerText = "Selected numbers: " + selectedNumbers.join(', ');
    } else {
        document.getElementById('latestOutput').innerText = "All numbers have been selected.";
    }
}

function resetSelection() {
    document.getElementById('latestOutput').innerText = "Selection reset. You can start over.";
    document.getElementById('selectedNumbersOutput').innerText = ""; // Clear selected numbers output
    selectedNumbers = [];
    availableNumbers = [];
}
</script>