## A Clojure Fusion of Symbolic and Data Driven AI

Huahai Yang, Ph.D.
<br>
Juji, Inc.

Note:

- Good morning. my name is Huahai Yang
- Today I will talk about a Clojure fusion of symbolic and data driven
  artificial intelligence

---

@snap[west]
@css[bio-about](Psychologist<br>Computer scientist)
<br><br><br>
@css[bio-about](Coding in Clojure since 2012)
@snapend

@snap[east bio]
@css[bio-headline](Huahai Yang)
<br>
@css[bio-byline](@fa[github pad-fa] huahaiy @fa[twitter pad-fa])
<br>
![Huahai](asset/img/huahai.png)
<br>
@css[bio-tagline](Cofounder & CTO<br>Juji Inc.)
@snapend

Note:

- I am academically trained as a psychologist.
- And I have worked professionally as a computer scientist, at places like IBM Research and IBM Waston.
- I have been coding primarily in Clojure since 2012
- Now I am a co-founder of Juji

---

### Juji Builds Chatbot Platform

- A challenging problem

Note:

- What does Juji do? Juji builds a platform for organizations to create
  chatbots, or conversational agents.
- Some of us know that building chatbots that talk like human is a challenging problem
- Some may even say that it requires AGI, or at least the ability to pass the Turing test
- You know, the test where a human cannot tell if she's talking with a human or a machine.

---

### Juji Builds Chatbot Platform

- It is not hard to pass Turing Test, done in 70s'
  - PARRY: 33 psychiatrists cannot tell it from paranoid patients

+++ PARRY sample

![Parry](asset/img/parry.png)

Note:

- Well, actually Turing test has already been passed a long time ago.
- PARRY, a chatbot developed by a psychiatrist at Stanford, did that in 1972.
- PARRY simulated a paranoid patient. It has a mental model, where it tracks the
  mental states such as the level of fear. It talks differently according to
  its mental states
- A panel of 33 psychiatrists can only tell it from real paranoid patients 48%
  of time, basically at chance level, meaning that PARRY has passed the Turing test.
- The lesson here is that, if you have a consistent and reasonable mental model,
  it is easy to build a chatbot that talks like a human.

---

@snap[north span-100]
### Juji Builds Chatbot Platform
@snapend

@snap[west span-60]
@ul[](false)
- It is harder to build **useful** chatbots
  - interview people to collect feedback
  - receive visitors to sites
  - screen job candidates
  - check up on trainees
  - help students learn
  - recommend books
@ulend
@snapend

@snap[east span-40]
![Juji chat](asset/img/juji-chat.png)
@snapend

Note:

- What's harder, is to make the chatbot also do something useful for human.
- That's what Juji's chatbots do, they have a purpose, an agenda.
- For example, here is a part of our bot's conversation with a gamer, after it
  has shown the gamer some game trailers. This is to collect data
  for one of our marketing research customers. As you can see, in addition to
  feedback to trailers, the bot also collects information about the gamer's
  gaming preference to help with analysis. It doesn't give up easily.
- There are many other use cases that chatbots have been deployed for:

---

@snap[north span-100]
### Juji Approach:<br>Symbolic + Data Driven
@snapend

@snap[west span-50]
@ul[](false)
- Symbolic system as the bones
- Data-driven component as the flesh
- Done in a Clojure DSL
@ulend
@snapend

@snap[east span-50]
![Juji DSL](asset/img/dsl.png)
@snapend

Note:

- We are able to build our bots to do these non-trivial tasks, because we
  developed a unique approach towards practical AI.
- We took a hybrid approach that integrates the so called traditional, symbolic AI
  with data driven, ML/DL based AI.
- where we use symbolic system as the bones, the data driven components as the
  flesh.
- All these are done in a Clojure domain specific language we developed.
- Here it is how DSL looks, and I will get to the detailed explanation latter.
- Before we dive in, let us step back, I will show you why we take this approach
  to AI.

---?image=asset/img/ai-summer-80.png

### AI Summer is Back

- Watson Jeopardy beats human
- AlphaGo beats human
- Many AI assistants on phone and in home
- Many commercial products in enterprises

Note:

- We all know that the AI summer is back. AI is in the news often these days.
- READ

---

### Rise of Deep Learning (DL)

- Recently hugely successful
- For many: @color[red](AI = DL)

![DL](asset/img/dl.png)

Note:

- A lot of these, are riding on the success of deep learning, neural networks
  that have many hidden layers.
- DL has revolutionized computer vision and image processing, with numerous
  applications. It can even be used to create digital arts.
- In many people's mind, AI is all about deep learning.
- So is it true? AI=DL? In the big scheme of AI, where does DL fit?

---

### DL Solves Perception Problem

@quote[Perception is the organization, identification, and interpretation of sensory information in order to represent and understand the presented information, or the environment.]

- DL maps raw data (pixels, text characters) into:
  - known labels (classification)
  - desirable numbers (regression)
  - fixed length vectors (embedding)

Note:

- It is my opinion, as well as some others, that DL mainly solves the perception problem.
- READ
- Look what DL does, READ
- These are all perceptual tasks.

---

@snap[north span-100]
### Perception Feels like Intelligence
@snapend

@snap[west span-40]
![Capablanca](asset/img/capablanca.jpg)
@snapend

@snap[east span-40]
![Bobby Fischer](asset/img/BobbyFischer.jpg)
@snapend

<br>

@snap[south list-content span-100]
@ul[](false)
- @size[12](Reporter: "How many moves do you see ahead while playing chess?")
- @size[12](Capablanca: "Only one, but it's always the right one.")
@ulend
@snapend

Note:

- People confuse perception with intelligence because many intellectual tasks
  can be solved as perceptual tasks in surprising ways.
- For example, playing chess is normally considered a task that requires a lot
  of intelligence, logical reasoning, thinking ahead a lot of steps, and so on.
- But that's not how chess masters solve it.
- Chess masters turn the task into a perceptual one, where there's not much
  reasoning involved, just pattern recognition.
- For example, Capablanca, considered one of the best chess player of all
  time, READ
- That's why master players can play with many people at the same time, walking
  around the room, look at the board and make a move almost immediately.
- That's also how alphago solved Go, a much more complex game.
- They have turn a search task into a perceptual task through extensive training.

---

@snap[north span-100]
### Perception is not yet Intelligence
@snapend

@snap[west]
![Cognitive Psychology](asset/img/cognitive-psychology.jpg)
@snapend

@snap[east]
<img src="asset/img/cognitive-psychology-toc.png" alt="Cognitive Psychology TOC" width="480"/>
@snapend

Note:

- Not all tasks requiring intelligence can be turned into perceptual tasks.
- If we look at any textbook on cognitive psychology, perception is just one
  chapter among many, that deals with topics such as attention, memory,
  mental model, knowledge representation, language, problem solving, reasoning,
  the list goes on.
- They are all part of human intelligence.

---

@snap[north span-100]
### Intelligence Cannot be Solved with Data Alone
@snapend

@snap[west list-content-concise span-40]
@ul[](false)
Bottom-up
    * data driven
    * sub-symbolic
@ulend
@snapend

@snap[east list-content-concise span-60]
@ul[](false)
Top-down
    * goal/hypothesis driven
    * symbolic (human-readable)
@ulend
@snapend

Note:

- Most of the mental processes listed above cannot be solved with data alone.
- Data driven process is a kind of bottom-up process, where raw sensory
  information, such as light, sound, enter from the environment into
  sensory organ, is then turned into a perception in the brain.
- This process itself is not accessible for human conscious, so we call these
  sub-symbolic process. Neural network can be thought of as an implementation of
  such a process.
- However, bottom-up process is not enough for intelligence. In fact, more than
  90% of information is lost by the time they arrive at brain for processing.
  So what brain constantly does, is to form hypothesis, or guesses about the
  environment, the meaning is based on what the brain already knows and expects.
- Such hypothesis or goal driven processes, are the focus of the so called
  "traditional AI", also knows as symbolic AI. Symbolic means human-readable representations.

---

### Time to Bring back Symbolic AI

- (Semi-)solving perception lays the foundation for symbolic AI
- The same forces leading to the rise of DL apply to symbolic AI
  - More powerful hardware, help graph search
  - More abundant realistic data, help knowledge base construction
  - Better software tools and practices

Note:

- To solve artificial intelligence, both bottom-up and top-down processes are
  necessary.
- With the rise of DL, we may say that the bottom-up perception problem is
  semi-solved. It's not entirely solved because what DL learned may not be of
  the same nature as human perception. But for many problems, we consider it is
  good enough.
- With such a more solid perceptual foundation than before, it is my opinion
  that now it is the time to bring back symbolic AI.
- The same forces leading to the rise of DL apply to symbolic AI as well.
- The most successful of symbolic AI were expert systems, basically large graph of
  production rules. A production rule is just an if-then statements.
- Many symbolic AI problems rely on solution to graph search problems, and graph
  search can leverage the latest advances in GPU hardware, just like DL does.
- Expert systems rely on large knowledge base, the construction of knowledge base
  should benefit from more abundant realistic data we have today.
- We also have better software tools and better engineering practices than
  before. These should help with building robust symbolic system.

---

### Trade-offs

- Data driven
  - Easy to defeat/abuse by adversaries (e.g. Tay)
  - Hard to debug and bend it to the creator's will
  - By design, unlikely to be fixable with data alone

- Symbolic
  - Easy to build rigid/brittle systems
  - Hard to develop, for it is hard for human to think like machines
  - In principle, fixable with *enough* human efforts

Note:

- There are weaknesses for both data-driven and symbolic approaches.
- The data driven approach rely on the quality of data, so an adversary can
  feed such system bad data to defeat or confuse the system. There are
  many papers in image processing demonstrating some human undetectable changes,
  for example, tweak a few pixels, can lead DL based vision system to give
  complete wrong results.
-

+++ DL is fooled

![Parry](asset/img/fool-dl.png)


---
### Two Roads to Integration

- Extract symbols out of sub-symbolic, then put symbols back
    - Mimic nature
    - Not yet practical

- Symbolic + sub-symbolic
    - Engineer's method
    - Practical today

---

### Symbolic + Data Driven

- Symbolic system as the bones
  - for its potential for growth and adaptability, despite the rigidity
- DL/ML component as the flesh
  - for its flexibility and ease of development, despite the obscurities

---

### Juji Platform

- Used for interviewing people
- 2X completion rate, 26% better quality responses

@quote[the whole time i was doing this survey it felt like i was talking to a friend and sharing the same common ground. i loved that i wish it didnt have to end]

@quote[very dynamic and very fluid conversation you have great quality thanks]

---

### Juji Architecture

![Uji architecture](asset/img/juji-architecture.png)

---

###  EDN Data all the Way

![Uji workflow](asset/img/juji-workflow.png)

1. User select chat template
2. User configure chat in GUI
3. Generate script from GUI
4. Chat: script compiles and runs

---

### Deftopic: the Building Block

- Topic: a set of rules

```clojure
(deftopic hello-world ; topic name
  []                  ; parameters

  []                  ; trigger
  ["Hello world!"])   ; action

```

@[1]
@[2]
@[4]
@[5]

---

### Production Rule

- Rule: trigger (if),  action (then) and associated followup topics
- Followup topics are primed when a rule fired

```clojure
[:1 hello hi hey howdy] ; trigger: an alternative pattern
["Nice to meet you!"]   ; action: a string output
(talk-about-wheather)   ; a followup topic invocation
```

@[1]
@[2]
@[3]

---

### Topic Compositions

- A topic may include rules of other topics

```clojure
(deftopic greetings
  []
  {:include-before [(morning-greetings)
                    (evening-greetings)]}

  [:1 hello hi hey howdy]
  ["Hello"])

```
@[3-4]

---

### Patterns

- Token based regular expressions

```clojure
[I love :1-. pizza]                  ; sequence pattern with a wild card
[I love ? [:1- pizza bacon sausage]] ; nesed sequences, inner is a multiple alternative
[:0. "I love pizza"]                 ; start pattern and a string pattern
```

@[1] sequence pattern with a wild card
@[2] sequence patterh with an one or nothing and a multiple alternative
@[3] start pattern and a string pattern, where no lemmatization is done

---

### ML Based Tag and Class Patterns

- Tags for annotating text, keywords for placeholders of content classes
- Parts of speech, phrases, and entities

```clojure
[he #pos/verb dog tree]               ; parts of speech tag
[she love :phrase/NP]                 ; noun phrase class
[I work at :entity/org]               ; organization entity class
[it will be done in :entity/duration] ; duration entity class
```

@[1]
@[2]
@[3]
@[4]

---

### DL/ML for Classification Functions

- Neural networks are universal **function** approximator, should be used as such

```clojure
[programming
 (input-in-this-category? "self-intro-relevance" 0.7)]
["You must be a smart person"]
```

@[2]

- Patterns are `and` together in a rule
- Rules are `or` together, so a topic matches a DNF

---

### DL for Similarity Based Matches

- Calculate similarity using Tensorflow sentence embedding

```clojure
[(> (max-similarity-score
     ["What does your product cost?"
      "How much does your product cost?"
      "What's the price of your product?"
      "How expensive is your product?"])
    0.9)]
```

---

### Roles

- ML/DL models cover broad cases
- Symbolic covers specific cases
  - misses by DL/ML
  - detailed refinement

```clojure
[(input-in-this-category? "self-intro-relevance"
                          0.7)]
([programming]
 "You must be a smart person."

 [art]
 "I enjoy art too."

 "Thank you for the introduction.")
```

@[1=2]
@[3-4]
@[6-7]
@[9]

---

### Meta-circularity

- Turn a topic into a function, then use the function in another topic

```clojure
[(create-topic-func
    custom/why-u-here :extract-why-u-here)
 "I see, you are here to "
 (exec-topic-func :extract-why-u-here)]
```

@[1-2]
@[4]


---

### Automatic Dialog Management

- REP is a declarative language
- System pushes topics around
  - Agenda queue
  - Ad-lib queue
  - Exception queue
  - Main stack

---

### Conclusion

- AI is not DL
- Symbolic + data driven = practical AI today
- Clojure is a great choice for doing so
  - Lisp was and still is the language of symbolic AI
  - Data orientation of Clojure makes it easy to integrate both

---

@snap[east span-50]
![QUESTIONS?](template/img/questions-4.png)
@snapend

@snap[west span-50]
Huahai Yang
<br>
Juji, Inc.
<br>
https://juji.io

@snapend
