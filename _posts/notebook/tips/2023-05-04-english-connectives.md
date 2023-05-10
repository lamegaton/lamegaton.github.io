---
layout: post
title: "[English] Connectives"
categories: tips
author: "Son Pham"
comments: false
mermaid: true
---

After many hours of googling, mermaid is finally run on Github Page, thanks to [Jojozhuang](https://jojozhuang.github.io/tutorial/jekyll-diagram-with-mermaid/). 

I may not write another note for mermaid so I put the info here. First, we need to add `mermaid: true` into our post layout. Second, we need to use div tag as below.
```html
<!--
    to use mermaid in Jekyll we need to wrap it with <div>
-->
<div class="mermaid">
    your_mermaid_chart
</div>

```

## connectives

<div class="mermaid">
flowchart LR
    ROOT[Connectives] --> A & B & C & D & E & F & G & H
    A[to show contrast] --> 
        AA[but, in contrast, conversely, however, still,<br> nevertheless, yet, on the other hand, <br> on the contrary, or, in spite of this, actually, in fact]
    B[to extend or amplify] --> 
        BB[and, also, besides, furthermore, too, <br> moreover, then, equally important, another]
    C[to show similarity] --> 
        CC[like, in the same manner, as so, similarly, likewise, coupled with this]
    D[order or sequence] --> 
        DD[first, second, finally, next, then, <br> to begin with, after, before, as soon as, in the end, gradually]
    E[to show results] --> 
        EE[as a result, so, accordingly, consequently, <br> thus, since, therefore, for this reason, because of this]
    F[purpose] --> 
        FF[for this purpose, with this in mind, for this reason]
    G[example] --> 
        GG[for example, to illustrate, for instance,<br> to be specific, such as, especially]    
    H[to draw conclusion] --> 
        HH[in summary, to sum up, to repeat, briefly,<br> in short, finally, on the whole, <br> therefore, as I have said, in conclusion, as you can see, to reiterate, to summarise]
    click A "{{page.url}}#contrast" _blank
    click B "{{page.url}}#addition" _blank
    click C "{{page.url}}#comparison" _blank
    click D "{{page.url}}#order-or-sequence" _blank
    click E "{{page.url}}#results" _blank
    click F "{{page.url}}#purpose" _blank
    click G "{{page.url}}#example" _blank
    click H "{{page.url}}#conclude" _blank
</div>

## examples
### contrast
1. **but**: She loves to cook, but she hates doing dishes.
1. **in contrast**: The first half of the book is dark and serious, in contrast, the second half is light and funny.
1. **conversely**: Some people believe that technology is the key to a better future, conversely, others believe that technology is the source of many problems.
1. **however**: I really want to go on vacation, however, I can't afford to take time off work right now.
1. **still**: It's been raining all day, but I still want to go for a walk outside.
1. **nevertheless**: The movie got terrible reviews, nevertheless, I still want to see it because I like the actors.
1. **yet**: I've been studying for hours, yet I still feel like I haven't learned enough.
1. **on the other hand**: Some people love to travel, on the other hand, some people prefer to stay close to home.
1. **on the contrary**: Many people believe that technology is making us more isolated. On the contrary, technology can actually help us connect with others around the world.
1. **or**: Would you like to go to the beach or go hiking in the mountains?
1. **in spite of this**: I'm not a big fan of spicy food, in spite of this, I ordered the extra spicy curry.
1. **actually**: I thought I was going to fail the test, but actually, I got an A.
1. **in fact**: I always thought that he was the older sibling, in fact, he's younger than I am.


### addition
1. **and**: And then we went to the store to buy some groceries.
2. **also**: Also, she's an amazing artist in addition to being a talented musician.
3. **besides**: Besides studying, I also work part-time to pay for my expenses.
4. **furthermore**: Furthermore, the new software update includes several new features that make it easier to use.
5. **too**: Too, I enjoy spending time with my friends and family.
6. **moreover**: Moreover, the restaurant not only has great food, but also has excellent service.
7. **then**: Then, I realized I had left my phone at home and had to go back to get it.
8. **equally important**: Equally important, we need to make sure that we stay within our budget when planning our trip.
9. **another**: Another factor to consider is the environmental impact of our choices.

### comparison
1. **Like**: Like his father, he's a great athlete.
2. **In the same manner**: In the same manner as her sister, she's also a talented musician.
3. **As so**: She was late for the meeting, as so, the other attendees had to wait for her.
4. **Similarly**: Similarly to her brother, she excels in math and science.

### order or sequence
1. **First**, I'm going to make a list of all the things I need to do today.
2. **Second**, I'll prioritize the items on the list based on their importance.
3. **Finally**, I'll start working on the tasks and check them off the list as I go.
4. **Next**, I'll focus on completing the most urgent tasks on the list.
5. **Then**, I'll take a break and grab some lunch before continuing with my work.
6. **To begin with**, I'd like to thank everyone for coming to the meeting today.
7. **After** the meeting, we can discuss any follow-up tasks that need to be completed.
8. **Before** we get started, let's review the agenda for today's meeting.
9. **As soon as** I finish this project, I'll be able to take some time off and go on vacation.
10. **In the end**, I was able to finish all of the tasks on my list and feel a great sense of accomplishment.
11. **Gradually**, I've been making progress towards my goal and feel more confident each day.

### results
1. **As a result**, he missed his flight and had to reschedule for the next day.
1. I am busy today, **so** I won't be able to join you for lunch.
1. The project is behind schedule, **accordingly**, we need to increase our efforts to catch up.
1. She didn't study for the exam, **consequently**, she failed it.
1. He forgot his phone at home, **thus**, he couldn't check his emails.
1. **Since** it's raining outside, we'll have to cancel the outdoor picnic.
1. He didn't wear a helmet while riding his bike, **therefore**, he was injured in the accident.
1. The software crashed repeatedly, **for this reason**, we need to update it.
1. He couldn't attend the meeting, **because of this**, he missed important information.

### purpose
1. **For this purpose**, I have prepared a detailed plan of action.
1. **With this in mind**, we need to consider all the possible outcomes before making a decision.
1. I cannot attend the meeting today. **For this reason**, I will be sending my colleague in my place.

### example
1. I have several hobbies, **such as** painting, playing guitar, and hiking.
2. I enjoy traveling to different countries, **for instance**, I recently went to Japan and fell in love with the culture.
3. There are many reasons why people should exercise, **to illustrate**, it can improve physical and mental health, boost energy levels, and reduce stress.
4. I need a new laptop, **for example**, I need it to have a long battery life and be lightweight for easy portability.
5. I want to make sure I'm being **specific** when I describe the project requirements to my team, so they can fully understand what is expected of them.
6. I love all kinds of music, but **especially** enjoy listening to jazz and classical music.

### conclude
- **In summary**, the project was a success and achieved all of its objectives.
- **To sum up**, the main points of the presentation are that we need to increase sales and improve customer satisfaction.
- **To repeat**, we cannot proceed with the project until we receive further instructions from management.
- **Briefly**, the report highlights the main challenges facing our industry and suggests potential solutions.
- **In short**, we need to cut costs and increase productivity if we want to remain competitive.
- **Finally**, I would like to thank everyone who contributed to the success of this project.
- **On the whole**, the feedback from customers has been positive, but there are some areas for improvement.
- **Therefore**, we recommend that the company invest in new technology to improve efficiency.
- **As I have said**, the proposal has the potential to generate significant revenue for the company.
- **In conclusion**, the evidence presented supports the hypothesis that climate change is caused by human activity.
- **As you can see**, the chart clearly illustrates the upward trend in sales over the past year.
