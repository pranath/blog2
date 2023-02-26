---
aliases:
- /opinion/2021/04/04/ai-human-preferences
categories:
- opinion
- deep-learning
date: '2021-04-04'
description: AI systems are being used everywhere, but often little work is done to
  gain a deeper understanding how and why they work. We have so much to gain from
  trying to look deeper inside these AI systems to understand them better.
image: https://github.com/pranath/blog/raw/master/images/aihuman.jpeg
layout: post
title: What AI can tell us about the hidden preferences of human beings

---


## Introduction

AI systems are increasingly being used in almost every area of human activity, from the online world, in streaming media, social media & online shopping - to the offline world, in policing, healthcare and other public services as well as many different physical industries such as water, energy, agriculture and manufacturing. These applications of AI are having a huge impact, often beyond what is commonly known to the public, both [positive](https://www.nature.com/articles/d41586-020-03348-4) and [negative](https://www.fast.ai/2017/11/02/ethics/).

Most work in the field is focussed on trying to use AI to solve a particular problem at hand, and if the problem is 'solved' then little more thought is often done. Much less work goes on into understanding the fundamental nature of the AI created to solve a particular problem. To some extent this is of course because the main motivation is to solve the problem, but another reason is often because AI systems i.e. artificial neural networks, are often incredibly complicated, are not directly created by humans - and so can actually be very difficult to understand the inner workings of. Questions such as How is it doing it? Why is it doing it? What has it learnt? are questions often not addressed - as long as the AI system seems to 'get the job done'.

It's certainly my belief that this much neglected area is worth far more work than it often gets, not only to allow us to understand the AI system at a deeper level, but that it might also give us new insights and understandings into the area the AI system is being applied to.

In this article I'm going to look at one particular area of AI application called *Recommendation Systems*. For a recent project, I created an AI system for recommending new books to readers. I then extended the project to study how this AI book recommendation system itself was working, and discovered what it had learnt about the hidden preferences of book readers.

## What are Recommendation Systems?
Recommendation systems are very common particularly in online services. For example, Amazon suggestions for alternative products, on Netflix suggestions for films, on Spotify for music, or on Facebook for the content you see on your newsfeed. All of these services and more use recommendation systems to suggest new content to people, but what are these systems and how do these actually work? 

A very simple approach might be to recommend the most popular items to people. Of course, popular items would probably appeal to many - but not to everyone. With modern AI based recommendation systems we can do much better than this, to make more personalised suggestions that are unique to each person. There are two main approaches to this: content-based filtering and collaborative filtering.

![](https://github.com/pranath/blog/raw/master/images/reccsystems.png "Types of Reccomendation Systems")

With *content-based filtering*, we look at the content a person has previously looked at (eg songs or films you have previously watched) as a basis to recommend new content. In this case, the AI system does the work here to understand what content is similar, for example what films are similar. This might be based on more obvious things such as the film genre, or which actors are in the film. However it can also be based on less obvious things that the AI can learn for itself about what makes films similar or different, things that are not given to the AI at all, but that the AI system can learn itself. These hidden aspects are called **latent factors**.

With *collaborative filtering*, we look at other people who are similar to us, and suggest items that they have liked, that we have not yet seen. Here the AI system does the work to understand which people are similar to us, as a basis to make suggestions. As a simple example, on a music service, we could find another listener who has listened to some of the same songs we have, find a song they have listened to that we have not, then recommend that to us. However, this simple strategy may not always be effective, just because 2 people like the same song, that does not always mean they would both like another song that one of them liked, let alone that both people are 'similar'? What makes people similar and different, might be based on things like the genre of music they liked, which artists etc. 

But what truly makes people similar or different in their preferences can also be based on less obvious things, more nuanced and subtle reasons, things people often do not perhaps even understand themselves, biases, etc that are hidden and unconscious, and yet drive and influence people's choices and behaviour. These hidden biases and influences are things not given to the AI at all, how could they be? and yet, they are things AI systems can still learn about for itself, which are again here called latent factors.

## Creating a book recommendation system
For my book recommendation system, I used the collaborative filtering approach. The data I used to create this system is the [Book Crossing dataset](http://www2.informatik.uni-freiburg.de/~cziegler/BX/) which is data on peoples book ratings of around 27,000 different books, from the Book Crossing community website, gathered in September 2004. There are around 28,000 users of this website who are from all over the world, and from a range of different ages. The key data is a table of individual ratings of a person (identified by a unique user id), a book and a the value of the rating (a number between 0-10).

![](https://github.com/pranath/blog/raw/master/images/rating_table.png "Ratings table data")

These user ratings are not exhaustive, i.e. every user has not rated every book. Note also there is no extra information about the books such as categories, or about each person such as their ages. But we don't actually need this extra data, we can create an AI collaborative filter based system (commonly called a 'model') that learns just from the table of users, books and ratings, to build up an understanding of the latent factors that uniquely describes each book, and each person. Once the model has been 'trained' on this data, and learnt these latent factors - the model can then use these latent factors to make recommendations for each person, about what new books they might like.

When the AI model learns, it doesn't directly see the real ratings - it just tries to make guesses about what the ratings should be. We then compare the guesses to the actual ratings we know, and give the model back some measure of accuracy, which the model then uses to improve its guesses in the next cycle. This training process repeats for many cycles. 

## Going down the rabbit hole: what is our book recommendation system actually doing?

So we now have a book recommendation system that can suggest new books to people. But we can if we choose, take things further. Simply from the data of book ratings and the learning process, the system has had to understand something more, about the implicit reasons certain people prefer certain books over others - and indeed perhaps about general qualities that drive these choices. These qualities might correspond to categories we might recognise as more obvious book genres, but they might also correspond to other qualities that are not commonly recognised as 'categories' yet might still be factors that drive people to prefer different books.

How might we try and understand these latent factors that drive people's preferences for books? 

We actually have 2 types of latent factors, normal factors and bias factors. Bias factors represent a general bias towards a book, either positive or negative. This will mean for that book, regardless if it would be generally a good suggestion for a person - if it has a negative bias it will be far less likely to be suggested. Similarly, if a book has a very positive bias, it might be more likely to be suggested to you, even if you would not normally read that kind of book i.e. you would not normally read that genre. We can think of bias then as some kind of measure of 'general popularity' of a book.

### Negative bias books

So these are the bottom 10 books with the most negative bias in the AI model:

- Wild Animus
- The Law of Love
- Blood and Gold (Rice Anne Vampire Chronicles)
- Gorky Park
- The Cat Who Went into the Closet
- Waiting to Exhale
- Night Moves (Tom Clancy's Net Force No. 3)
- Ruthless.Com (Tom Clancy's Power Plays)
- Ground Zero and Beyond
- Say Cheese and Die! 

Let us look at the 2 books with the most negative bias, 'Wild Animus' and 'The Law of love'. So what is Wild Animus about? The synopsis reads:

>"Sam Altman is an intense young man with an animal energy whose unleashed and increasingly unhinged imagination takes him first to Seattle and then farther north, to the remote Alaskan wilderness. ..."

This book does have many many online reviews, on the whole which can be summarized by the review [What the hell is Wild animus?](https://litreactor.com/columns/what-the-hell-is-wild-animus). The review concludes with a quote from a goodreads reviewer:

>"I'll tell you the ending. A column of lava erupts from beneath his feet while he is dressed in a goat costume and wolves are in mid-air tearing him apart."

On the whole it seems, Wild Animus seems to provoke a very unfavourable response from most reviewers! The next most negative bias book is 'The law of love', it's synopsis reads:

>"After one night of passion, Azucena, an astroanalyst in twenty-third-century Mexico City, is separated from her Twin Soul, Rodrigo, and journeys across the galaxy and through past lives to find her lost love, encountering a deadly enemy along the way..."

As it happens this book has as many positive reviews as negative online, in fact few reviews seem neutral at all. So this is not universally seen as a bad book, by humans who post reviews online anyway. Nevertheless, our AI model regards this as a book that should not really be suggested to anyone. Is that because the book seems to be so divisive? and perhaps there are other books that are 'safer bets'? Either way, the computer says no.

### Positive bias books

Let's now look at the top 10 books with the most positive bias in the AI model:

- The Lovely Bones: A Novel
- Harry Potter and the Goblet of Fire
- The Da Vinci Code
- Harry Potter and the Prisoner of Azkaban 
- The Secret Life of Bees
- Harry Potter and the Sorcerer's Stone 
- Harry Potter and the Chamber of Secrets 
- Where the Heart Is 
- To Kill a Mockingbird
- The Red Tent

So looking in more detail at the 2 books with the most positive bias we have 'The lovely bones' and 'Harry Potter and the Goblet of Fire'. So the synopsis of "The lovely bones" is as follows:

>"It is the story of a teenage girl who, after being raped and murdered, watches from her personal Heaven as her family and friends struggle to move on with their lives while she comes to terms with her own death. "

This book has a large number of very favourable reviews, in fact it was hard to find a very negative review of this book at all. [The New York Time's review](https://www.nytimes.com/2002/07/14/books/what-remains.html) perhaps sums up well the general sentiment felt by most reviewers of this book:

>"...Sebold deals with almost unthinkable subjects with humor and intelligence and a kind of mysterious grace. The Lovely Bones takes the stuff of neighborhood tragedy -- the unexplained disappearance of a child, the shattered family alone with its grief -- and turns it into literature..."

So we can perhaps appreciate some of the reasons perhaps why the AI model thinks this is a good book to recommend to anyone, regardless of what their normal reading preferences might be. The second most positively biased book is "Harry Potter and the Goblet of fire". Being one of a series of some of the most popular books of all time - this is perhaps not surprising at all that the AI model thinks this would be a good book to recommend to most people, regardless of their normal reading preferences.

### Looking at other latent factors

So for the remaining latent factors, we actually have 50 of them for each of our 27,000 books - so quite a few! However we can use a process called *dimensionality reduction* to actually reduce these down, to the 2 most important latent factors for all books. We can then plot each book on a graph, with the measure that book has for each of these 2 key latent factors.

![](https://github.com/pranath/blog/raw/master/images/factors0-1.png "Key latent factor 1 (horizontal axis) and factor 2 (vertical axis) for 50 books")

A bigger view of this image of latent factors 1 & 2 can be seen [here](https://livingdatalab.com/images/factors0-1.png)

Here we can see 50 books plotted. On the horizontal axis that is a measure of how much of latent factor 1 each book has. On the vertical axis, that is a measure of how much of latent factor 2 each book has.

Let's look into latent factor 1, which is the strongest latent factor used by the AI model to make book recommendations. 

### Books with high values for latent factor 1

We can see in the bottom right corner of the chart 'The lovely bones'. This has one of the highest measures of factor 1, because it is one of the furthest to the right. We also know from our look at bias factors, that this is the book with the strongest positive bias latent factor as well i.e. a generally popular book. Let's also note it falls into the categories of 'Crime, Thriller, Mystery'.

Looking at another book with a high factor 1, in the top right we have 'Good in Bed'. The synopsis of the book is:

>"It tells the story of an overweight Jewish female journalist, her love and work life and her emotional abuse issues with her father."

It generally also has good reviews, and would fall into the category of 'Women's fiction'. Let's look at a third book with a high factor 1, "The life of Pi". The synopsis of this book is:

>"After the tragic sinking of a cargo ship, a solitary lifeboat remains bobbing on the wild, blue Pacific. The only survivors from the wreck are a sixteen year-old boy named Pi, a hyena, a zebra (with a broken leg), a female orang-utan and a 450-pound Royal Bengal tiger."

Again this book generated very good reviews, was very popular, and might fall into the category of 'Contemporary fiction'. What are some common things to note about all of these books with a high latent factor 1?

- They are all very popular and have great critical acclaim
- 2 of these books turned into films, and the third is currently being adapted for film.
- All 3 have a theme of a huge personal tragedy, which the protagonist is successful in overcoming and rising above by themselves

So lets bear this in mind, while we look at books with the lowest latent factor 1.

### Books with low values for latent factor 1

Books with low values for factor one are on the far left of the chart. For example we have 'A painted house' the synopsis of this being:

>"A Painted House is a moving story of one boy's journey from innocence to experience, drawn from the personal experience of legendary legal thriller author John Grisham"

Let's also note this would fall into the categories of  'Contemporary fiction, mystery'. Looking at another book with a low factor 1 'The street lawyer', the synopsis being:

>"...about an attorney who leaves his high-priced firm to work for the less fortunate."

This also seems to be another book by John Grisham, that would fall into categories such as 'Thriller, Mystery'. Looking at Grisham's work, how might we characterise his work more generally? He is well known for writing legal thrillers, and themes such as 'the triumph of the underdog', however A painted house seems not to quite fit these themes, an exception - so why is it here? A theme that might link both is 'the triumph of working together' in the case of the legal thrillers it's the lawyer, the legal system his collaborators, in 'a painted house' its the family that needs to pull together to triumph, as explained in [this review](https://www.enotes.com/topics/painted-house/themes):

>"...The primary theme is the importance of family: only by pulling together does the family achieve even moderate success"

In fact when we look at the other books with the lowest factor 1, on the far left of the chart, they pretty much are all John Grisham legal thriller books such as:

- The Pelican brief
- The Brethren
- The Summons
- The Firm

### So what is latent factor 1?

Let's now consider what factor 1 might actually be about. Given most of these books, regardless of having a low or high value of factor 1, have all been popular and successful - so popularity I would argue has nothing to do with what factor 1 is really about. 

Based on what we have learnt about these books so far, I would speculate that latent factor 1 might represent a measure of  **'The triumph of the group vs the triumph of the individual'** as a theme-axis. So, low values of factor 1 would correspond to 'The triumph of the group' type themes, and high values of factor 1 would correspond to 'The triumph of the individual' type themes for books.

Remember the AI model is given no information about book categories, authors, genres, themes etc. All the AI has to learn from is the ratings between users and books - that's all. Not only has our AI model discovered this particular axis theme by itself from very limited information, but it has done so because the AI model has judged that this theme-axis, whatever it is, is one of the most useful for the purposes of making good book recommendations to people.

## Discussion 
So how do we make sense of our findings? We can't conclusively say that my suggested 'triumph of the group vs triumph of the individual' theme-axis is generally true, or the key hidden factor for understanding generally why people prefer certain books over others. Firstly, it's based on an inevitably limited data set of books, people and ratings. Perhaps the people who made those ratings are not representative of the general population? Secondly, we only randomly chose 50 books to plot for our latent factors. What if we randomly picked a different set of 50 books, would we see the same kind of themes for latent factor 1, or something else? If the 'triumph of the group vs triumph of the individual' theme axis does appear to be a key factor over many more books and people - why is this the case? and what does it suggest about human beings more generally? However these are questions that could be further investigated, researched, and better answered - with more time, and the conclusions of which could potentially be very interesting indeed.

What we can say is that from very limited information, looking at a limited number of books, and looking at some of its latent factors such as biases and the main key factor - this AI model seems to have discovered many relationships we could recognise as humans such as 'generally popular books' and 'generally awful books'. The interpretation of the key latent factor as 'triumph of the group vs triumph of the individual' as a theme-axis is of course very speculative at this stage, and yet very intriguing! Would you come to a different conclusion looking at the books at either end of the axis of latent factor 1 on the chart? What do you think latent factor 1 on the horizontal axis is all about? What do you think latent factor 2 on the vertical axis is about?  I'd love to hear your feedback and thoughts on this, so do feel free to comment below.

## Conclusion

In this article I've tried to highlight a few key themes: that AI is being used everywhere, that little work is often done to understand how and why these AI systems work, and that we have so much to gain by actually trying to look inside and understand these AI systems better. I'd also argue this is becoming more and more important, given the growing impact of these increasingly powerful systems on our world and human life.

Looking inside these AI systems, even though not straightforward - gives us the chance to know more about what they are really doing and why, and can give us intriguing hints about the domains in which they are used, which I have tried to illustrate with my book recommendation project.

When these AI systems are used in the domain of human choices, the potential is there hidden within these systems to perhaps discover new insights, and pose new questions about ourselves and our choices, that we may have never even considered or knew to ask. Perhaps by looking a little deeper into AI, we can see a little deeper into ourselves.
