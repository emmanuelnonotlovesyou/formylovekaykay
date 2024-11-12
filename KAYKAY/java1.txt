// Text for the typewriter effect in the final poem screen
const poemText = `Kay Kay, you are a dream in bloom,
A gentle light that fills the room.
Your smile, a spark that wakes the skies,
Your laughter, soft as lullabies.

The sun might rise, the stars may shine,
But none compare to you, divine.
With every glance, my heart does sway,
More in love, day by day.

Your beauty’s rare, your spirit kind,
A precious soul, a brilliant mind.
To hold you close, to call you mine,
Makes every moment feel divine.

Will you be mine forever, my love?`;

// Variables to capture her answers
let likesAboutEmmanuel = "";
let dislikesAboutEmmanuel = "";
let wouldGoWithEmmanuel = "";

// Function to move to the next screen
function nextScreen(screenId) {
    document.querySelectorAll('.screen').forEach(screen => screen.style.display = 'none');
    document.getElementById(screenId).style.display = 'block';
}

// Function to show a message based on answer and then continue
function showMessageThenContinue(screenId, message, answer) {
    alert(message === 'aww' ? "Aww, that's so sweet!" : "Wow, haha!");

    // Capture answer for whether she'd go with Emmanuel
    wouldGoWithEmmanuel = answer;
    
    nextScreen(screenId);
}

// Function to save her likes about Emmanuel
function saveLikesAboutEmmanuel() {
    likesAboutEmmanuel = document.getElementById("likes-about-emmanuel").value;
    nextScreen('screen9');
}

// Function to save her dislikes about Emmanuel
function saveDislikesAboutEmmanuel() {
    dislikesAboutEmmanuel = document.getElementById("dislike-textarea").value;
    nextScreen('screen10');
}

// Function to show the answer box if "Yes" is selected for dislikes
function showAnswerBox(screenId, answerBoxId) {
    document.getElementById(answerBoxId).style.display = 'block';
}

// Function to display final message based on "Will you be with Emmanuel officially?" answer
function showFinalMessage(answer) {
    nextScreen('screen12'); // Go to the final screen
    const heading = document.getElementById("final-heading");

    if (answer === 'yes') {
        heading.innerText = "Congratulations, Emmanuel is officially yours! 🎉❤️❤️❤️";
    } else {
        heading.innerText = "Wow, haha!";
    }

    // Trigger typewriter effect for the final poem text
    typeWriterEffect("poem-text", poemText, 50);

    // Log answers to the console (for your review)
    console.log("Kay Kay's Answers:");
    console.log("Likes about Emmanuel:", likesAboutEmmanuel);
    console.log("Dislikes about Emmanuel:", dislikesAboutEmmanuel || "No dislikes mentioned");
    console.log("Would go with Emmanuel:", wouldGoWithEmmanuel);
}

// Typewriter effect function
function typeWriterEffect(elementId, text, speed) {
    let index = 0;
    const element = document.getElementById(elementId);
    element.innerHTML = ""; // Clear any existing text

    function type() {
        if (index < text.length) {
            element.innerHTML += text.charAt(index);
            index++;
            setTimeout(type, speed); // Delay for typing speed
        }
    }
    type();
}

// Initialize the first screen
nextScreen('screen1');
