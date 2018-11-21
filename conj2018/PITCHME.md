## A Clojure Fusion of Symbolic and Data Driven AI

Huahai Yang
<br>
Juji, Inc.

---

### AI is Back

- Watson Jeopardy
- AlphaGo beats human
- Many AI assistants on phone and in home
- Many commercial products in enterprises

---

### Rise of Deep Learning (DL)

- Neural networks with many layers
- Recently hugely successful
- For many: @color[red](AI = DL)

---

### DL Solves Perception Problem

@quote[Perception is the organization, identification, and interpretation of sensory information in order to represent and understand the presented information, or the environment.]

- DL maps raw data into:
  - known labels (classification)
  - desirable numbers (regression)
  - fixed length vectors (embedding)

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

---

### Perception may Feel like Intelligence

- Intellectual problems may be solved in surprising ways as perceptual problems

![Bobby Fischer](asset/img/BobbyFischer.jpg)


---

@snap[north span-100]
### Perception Cannot be Solved with Data Alone
@snapend

@snap[west list-content-concise span-50]
@ul[](false)
Bottom-up processing
    * data driven
    * sub-symbolic
@ulend
@snapend

@snap[east list-content-concise span-50]
@ul[](false)
Top-down processing
    * goal/hypothesis driven
    * symbolic (human-readable)
@ulend
@snapend

---

### Time to Bring back Symbolic AI

- Most successful were expert systems: a network of production rules
- (Semi)solving perception lays the foundation for symbolic AI
- The same forces leading to the rise of DL apply to symbolic AI
  - More powerful hardware
  - Better software tools
  - More abundant data

---

### Weaknesses of Data Driven vs Symbolic Systems

Data driven
  - Easy to defeat/abuse by adversaries
    - Tay
  - Hard to debug and bend it to the creator's will
  - By design, unlikely to be fixable

Symbolic
  - Easy to build rigid/brittle systems
  - Hard to develop, for it is hard for human to think like machines
  - Fixable with *enough* human efforts

---
### Two Roads to Integrate Symbolic with Sub-symbolic

1. Extract symbols out of sub-symbolic, then put symbols back
    - Mimic nature
    - Not yet practical

2. Symbolic + sub-symbolic
    - Engineer's method
    - Practical today

---

### Practical AI = Symbolic + Data Driven

- Symbolic system as the bones
  - for its potential for growth and adaptability, despite the rigidity
- DL/ML component as the flesh
  - for its flexibility and ease of development, despite the obscurities

---

### Build a Conversational Agent Platform

- It is easy to pass Turing Test: been done in 70s'
  - Parry
- It is harder to build **useful** conversational agents

---

### REP: a Conversational Agent Authoring Language

- Responsible Empathetic Persona, used for interview/surveys
- 2x completion rate, 26% better quality responses

@quote[the whole time i was doing this survey it felt like i was talking to a friend and sharing the same common ground. i loved that i wish it didnt have to end]

@quote[very dynamic and very fluid conversation you have great quality thanks]

@quote[You are my new best friend Juji!]


---

### Deftopic: the Building Block

- Topic: a set of rules

```clojure
(deftopic hello-world
  []

  []
  ["Hello world!"])

```

@[1]
@[2]
@[4]
@[5]

---

### Rule

- Rule: Trigger (if),  Action (then) and Followup Topics
- Followup topics are primed when a rule fired

```clojure
[:1 hello hi hey howdy]
["Nice to meet you!"]
(talk-about-wheather)
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
  {:include-before [(norning-greetings)
                    (evening-greetings)]})

 [:1 hello hi hey howdy]
 ["Hello"]

```
@[3-4]

---

### Patterns

- Just data, token based regular expressions

```clojure
[I love :1-. pizza]
[I love ? [:1- pizza bacon sausage]]
[:0. "I love pizza"]
```

@[1] sequence pattern with a wild card
@[2] sequence patterh with an one or nothing and a multiple alternative
@[3] start pattern and a string pattern, where no lemmatization is done
---

### ML Based Tag and Class Patterns

- Tags for annotating text, keywords for placeholders of content classes
- Parts of speech, phrases, and entities

```clojure
[he #pos/verb dog tree]
[she love :phrase/NP]
[I work at :entity/org]
[it will be done in :entity/duration]
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
 (input-in-this-category?
   "self-intro-relevance"
   0.7)]
["You must be a smart person"]
```
- Patterns are implicitly `and` together in a rule
- Rules are `or`ed together, so a topic matches a DNF

---

### DL for Similarity Based Matches

- Calculate similarity based on Tensorflow sentence embedding

```clojure
[(> (max-similarity-score
     ["What does your product cost?"
      "How much does your product cost?"
      "What's the price of your product?"
      "How expensive is your product?"])
    0.9)]
```
---

### Roles of ML/DL vs. Symbolic

- ML/DL models cover broad cases
- Symbolic covers specific cases
  - misses by DL/ML
  - detailed refinement
```clojure
[(input-in-this-category?
   "self-intro-relevance" 0.7)]
([programming]
 "You must be a smart person."

 [art]
 "I enjoy art too."

 "Thank you for the introduction.")
```
- Branched rule is essentially a decision tree

@[1-2]
@[3-7]
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
- REP compiler can be called at runtime, so topics may even be generated on the fly

---

### Automatic Dialog Management

- REP is a declarative language where system controls the flow
- Topics are pushed around as data
  - Agenda queue
  - Ad-lib queue
  - Exception queue
  - Main stack

---

### Putting Together: Juji Architecture



---

###  Data all the Way

1. User select template
2. User configure chat
3. Generate script from configuration
4. User chat: script compiles
5. User chat: script runs
6. Chat results

---

### Conclusion

- Clojure is a good choice for doing practical AI
  - Lisp was and still is the language of symbolic AI
  - Data orientation of Clojure makes it easy to integrate symbolic and data-driven approach

---

@snap[east span-50]
![QUESTIONS?](template/img/questions-4.png)
@snapend

@snap[south-west ]
Huahai Yang
Juji, Inc.
https://juji.io

@snapend
