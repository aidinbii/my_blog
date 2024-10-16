+++
title = "Randomizer (10)"
author = ["Aidin Biibosunov"]
lastmod = 2024-10-16T15:30:59+02:00
tags = ["teaching", "tools"]
categories = ["teaching"]
draft = false
type = "teaching"
+++

<input type="number" id="numberInput" placeholder="Enter the number of selections" min="1">
<button onclick="selectRandomStudent()">Select Random Student</button>
<button onclick="resetSelection()">Reset Selection</button>

<div id="latestOutput" style="margin-top: 20px; font-weight: bold;"></div>
<div id="selectedStudentsOutput" style="margin-top: 10px; font-weight: bold;"></div>

<script>
let selectedStudents = [];
let availableStudents = [
        "Адылбекова Нурайым ",
        "Алыбеков Нурали",
        "Айтымбетова Шайыма",
        "Алымбекова Назик",
        "Алмазбек уулу Мухаммад",
        "Арстанбеков Асанбек",
        "Арыстанбекова Амира",
        "Асхадова София ",
        "Белекова Сымбат",
        "Дюшенкулов Урмат",
        "Жайлообеков Актан ",
        "Жумабекова Аделя",
        "Жумабеков Кутман",
        "Исаков Ибрахим",
        "Исманбекова Касиет ",
        "Кадыров Баэл ",
        "Канатбекова Динара ",
        "Муканова Адеми",
        "Мырзабекова Эльвиза",
        "Нышанбаева Юсра",
        "Орозалиева Мария",
        "Токталиев Ислам",
        "Шарыпбекова Айдана"
];

function getRandomStudent() {
    if (availableStudents.length === 0) {
        return null; // No more students available
    }
    const randomIndex = Math.floor(Math.random() * availableStudents.length);
    return availableStudents.splice(randomIndex, 1)[0]; // Remove and return the selected student
}

function selectRandomStudent() {
    const N = parseInt(document.getElementById('numberInput').value, 10);

    if (isNaN(N) || N < 1) {
        document.getElementById('latestOutput').innerText = "Please enter a valid integer greater than 0.";
        return;
    }

    if (selectedStudents.length === 0) {
        // Initialize available students array when the selection starts
        availableStudents = [
        "Адылбекова Нурайым ",
        "Алыбеков Нурали",
        "Айтымбетова Шайыма",
        "Алымбекова Назик",
        "Алмазбек уулу Мухаммад",
        "Арстанбеков Асанбек",
        "Арыстанбекова Амира",
        "Асхадова София ",
        "Белекова Сымбат",
        "Дюшенкулов Урмат",
        "Жайлообеков Актан ",
        "Жумабекова Аделя",
        "Жумабеков Кутман",
        "Исаков Ибрахим",
        "Исманбекова Касиет ",
        "Кадыров Баэл ",
        "Канатбекова Динара ",
        "Муканова Адеми",
        "Мырзабекова Эльвиза",
        "Нышанбаева Юсра",
        "Орозалиева Мария",
        "Токталиев Ислам",
        "Шарыпбекова Айдана"
        ];
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

    // Now update the output to reflect all selected students, adding <br> after every 4th student
    outputText = selectedStudents.map((student, index) => {
        return student + ((index + 1) % N === 0 ? '<br>' : ', ');
    }).join('');

    document.getElementById('selectedStudentsOutput').innerHTML = "Selected students:<br>" + outputText;
}

function resetSelection() {
    document.getElementById('latestOutput').innerText = "Selection reset. You can start over.";
    document.getElementById('selectedStudentsOutput').innerHTML = ""; // Clear selected students output
    selectedStudents = [];
    availableStudents = [
        "Адылбекова Нурайым ",
        "Алыбеков Нурали",
        "Айтымбетова Шайыма",
        "Алымбекова Назик",
        "Алмазбек уулу Мухаммад",
        "Арстанбеков Асанбек",
        "Арыстанбекова Амира",
        "Асхадова София ",
        "Белекова Сымбат",
        "Дюшенкулов Урмат",
        "Жайлообеков Актан ",
        "Жумабекова Аделя",
        "Жумабеков Кутман",
        "Исаков Ибрахим",
        "Исманбекова Касиет ",
        "Кадыров Баэл ",
        "Канатбекова Динара ",
        "Муканова Адеми",
        "Мырзабекова Эльвиза",
        "Нышанбаева Юсра",
        "Орозалиева Мария",
        "Токталиев Ислам",
        "Шарыпбекова Айдана"
    ];
}
</script>