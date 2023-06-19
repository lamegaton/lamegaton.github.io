---
layout: page
title: CountDown
permalink: /count/
description: Hi, my name is Son Pham. One of my hobby is learning new things. 
I make this blog to share with you my long journey.
meta: 
---
<style>
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
</style>

![Moutain Tree](https://raw.githubusercontent.com/lamegaton/lamegaton.github.io/gh-pages/_posts/notebook/assets/tree_n_mt.png#centerImg)


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


<script>
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