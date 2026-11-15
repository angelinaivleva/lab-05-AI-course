# Lab 05 — Conclusion

<!--
Read this before you write.

This file is graded by your instructor, by hand, and it is worth 6 of the 15 points.

- Type it yourself. Do not use a chatbot, an AI assistant, an AI autocomplete or a "rewrite my
  text" tool for any part of it, not even for grammar. English that is plain and a little
  clumsy but yours is better than polished text that is not.
- Use your own numbers. Every number you quote must be one your own notebook printed. Copy
  the number exactly as it appeared. A number your notebook did not print is marked as wrong.
- Answer in your own words, about 80-200 words per question. A short answer that uses your
  numbers beats a long answer that could have been written by anyone.
- Delete these comment lines if you like. Keep the three headings and the last line.
-->

## 1. Which layer changed your results the most?

Give the numbers before -> after for that layer (correct / wrong / no answer, out of 20) and say
whether it changed what the agent *can do* or only what it *admits*. If no layer changed the
number of correct answers, say so and explain what the layers did change instead.
Before: 16 right, 4 wrong, 4 no answer
After: 18 right, 6 wrong, 0 no answer
I think its both (1st and 3rd) as the amount of right answer started to grow. Firstly, on first layer model was trying to learn based on wrong answers, so the probability of finding right answer grows with the amoung of attempts, however even though model solved questions with error right, it made other 2 question wrong (questions 21 and 22)(1st).Secondly, the second layer hasn't worked and its results stayed the same as it was on first one. Thirdly, it stopped write imaginary numbers if the data cell was empty (3rd). 


## 2. One failure the full harness did not fix

Pick one question that the full harness (layer 3) still gets wrong or refuses. Give its id
(q01 ... q20). Open its trace in the notebook: at which step did it go wrong, and what did
the model do instead? Name one thing you would add to the harness, and what it would cost
(extra model calls, tokens, time, or a new way to fail).

There was a problem with ['q08', 'q11', 'q17', 'q21'] and i will take q18 as an example. The model called get_series and it returned correct numbers, however on step where calculations were proccesed it made a mistake (it added divination by 100 and changed order of nums). As a result we get 0.055, but then it made another error and converted it to percentage wrongly with 0.55$ as an answer. Then there was attempt to fix it, but error rose again and the final answer was unverified. So i suppose it sould be better to send something like quesstion to get approve if numbers and calculations are correct, nevertheless it requires additional call for each question => more tokens; and also it can create another way to made a mistake as it can decline right anser or vice versa. 

## 3. Workflow or agent for the monthly ranking?

Dala Insight wants to publish, every month, "which region is highest and which is lowest on one
indicator in one year". Would you ship the fixed workflow or the agent? Use the accuracy, the
number of model calls, the tokens and the time you measured in Part 1. Then say in one sentence
what kind of question would make you choose the other one.

I would choose worflow and the question for eqch month is the same, the only changes are year and data. Also its more correct in differ to agent (workflow has 13/15, when 9/15). It spend less tokens (3852 and 19835) which is significant characteristic, and time is also beyyer in almost 3 times. In colclusion, agent is better when you dont know the form of the question, in such cases workflow works worse or maybe even not at all

---

I wrote this file myself, without any AI tool.
