---
layout: page
title: CountDown
permalink: /count/
description: Hi, my name is Son Pham. This is a countdown for my goal. It is 10000 hours.
author: Son Pham
keywords: son pham, lamegaton, countdown, js
---

<style>
.day {
  display: flex;
}
.hour-block {
  width: 20px;
  height: 30px;
  background-color: gray;
  margin-right: 1px;
}
.hour-block.passing {
  background-color: orange;
}
.hour {
  display: flex;
}
.minute-block {
  width: 5px;
  height: 20px;
  background-color: gray;
  margin-right: 1px;
}
.minute-block.passing {
  background-color: orange;
}
.minute {
  display: flex;
}
.second-block {
  width: 3px;
  height: 20px;
  background-color: gray;
  margin-right: 1px;
}
.second-block.passing {
  background-color: orange;
}
#countdown {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
.day-block {
  width: 10px;
  height: 10px;
  background-color: #ddd;
  margin: 1px;
}
.passed {
  background-color: lightsalmon;
}
.remaining {
  background-color: whitesmoke;
}

</style>

<p id="quote" style="font-family:'Courier New'">"Time is a valuable thing."</p>

<div id="day" class="day">
  <!-- Blocks representing each hour -->
</div>
<br>
<div id="hour" class="hour">
  <!-- Blocks representing each minute -->
</div>
<br>
<div id="minute" class="minute">
  <!-- Blocks representing each second -->
</div>
<br>
<div id="countdown"></div>
</br>
<p id="ps" style="font-family:'Courier New'">P/s: Many thanks to my family, friends, relatives and strangers who give me warm hugs, hot meals, and great experiences. We die every night and reborn the day after. We cannot let the small things in life burry our hope, our solidarity. Let's stand up and start again, shall we?"</p>


<script>
  const url = 'https://raw.githubusercontent.com/JamesFT/Database-Quotes-JSON/master/quotes.json';

function getQuote(url) {
  return fetch(url)
    .then(response => response.json())
    .then(data => {
      return data;
    });
}

let quote;
let i;

getQuote(url)
  .then(data => {
    quote = data;
		i = Math.floor(Math.random() * quote.length);
		document.getElementById('quote').innerHTML = `${quote[i].quoteText} - ${quote[i].quoteAuthor}`;
  })
  .catch(error => {
    console.log('An error occurred:', error);
  });

function updateClock() {
  const currentTime = new Date();
  const currentHour = currentTime.getHours();
  const currentMinute = currentTime.getMinutes();
  const currentSecond = currentTime.getSeconds();

  updateHours(currentHour);
  updateMinutes(currentMinute);
  updateSeconds(currentSecond);
}

function updateHours(currentHour) {
  const dayContainer = document.getElementById('day');

  // Remove existing blocks
  while (dayContainer.firstChild) {
    dayContainer.firstChild.remove();
  }

  // Create new blocks
  for (let hour = 0; hour < 24; hour++) {
    const hourBlock = document.createElement('div');
    hourBlock.className = 'hour-block';

    if (hour < currentHour) {
      hourBlock.classList.add('passing');
    }

    dayContainer.appendChild(hourBlock);
  }
}

function updateMinutes(currentMinute) {
  const hourContainer = document.getElementById('hour');

  // Remove existing blocks
  while (hourContainer.firstChild) {
    hourContainer.firstChild.remove();
  }

  // Create new blocks
  for (let minute = 0; minute < 60; minute++) {
    const minuteBlock = document.createElement('div');
    minuteBlock.className = 'minute-block';

    if (minute < currentMinute) {
      minuteBlock.classList.add('passing');
    }

    hourContainer.appendChild(minuteBlock);
  }
}

function updateSeconds(currentSecond) {
  const minuteContainer = document.getElementById('minute');

  // Remove existing blocks
  while (minuteContainer.firstChild) {
    minuteContainer.firstChild.remove();
  }

  // Create new blocks
  for (let second = 0; second < 60; second++) {
    const secondBlock = document.createElement('div');
    secondBlock.className = 'second-block';

    if (second < currentSecond) {
      secondBlock.classList.add('passing');
    }

    minuteContainer.appendChild(secondBlock);
  }
}

function updateCountdown() {
  const startDate = new Date("2023-04-18");
  const endDate = new Date("2024-09-01");
  const countdownContainer = document.getElementById("countdown");
  const currentDate = new Date();

  const remainingDays = Math.ceil((endDate - currentDate) / (1000 * 60 * 60 * 24));

  countdownContainer.innerHTML = "";

  for (let i = 0; i < remainingDays; i++) {
    const dayBlock = document.createElement("div");
    dayBlock.classList.add("day-block");

    if (startDate <= currentDate) {
      dayBlock.classList.add("passed");
    } else {
      dayBlock.classList.add("remaining");
    }

    countdownContainer.appendChild(dayBlock);
    currentDate.setDate(currentDate.getDate() - 1);
  }
}

// Update clock immediately
updateClock();
setInterval(updateClock, 1000);

// Update countdown immediately
updateCountdown();
setInterval(updateCountdown, 1000);

</script>
