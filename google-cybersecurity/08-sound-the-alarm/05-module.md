## AI in cybersecurity basics

AI refers to computer programs that can do cognitive tasks normally tied to human intelligence and we can use it to automate stuff like drafting emails summarizing info and helping analyze data. Gen AI is a specific type that generates new content like text images or other media tools like Gemini ChatGPT and Copilot fall under this

Some ways gen AI helps a cybersecurity professional

- creating content like fake data sets to test tools or lists of best practices
- analyzing large amounts of info quickly like summarizing reports or meeting transcripts
- answering detailed questions about threats like malware and ransomware
- simplifying daily tasks like checking if an email looks like phishing

AI is a double edged sword though since as it becomes more common attackers can also use it to launch more sophisticated attacks evade detection and exploit weaknesses so understanding both sides of it is important

## TCREI prompting framework

To get good output from a gen ai tool i need to follow a framework called TCREI which stands for task context references evaluate and iterate the trick to remember it is Thoughtfully Create Really Excellent Inputs

Task is basically what i want the model to do and it breaks down into persona and format persona means what expertise the ai should draw from like acting as a professional speech writer or someone with 15 years experience format means how i want the output like a list short sentences or table

Context means giving enough detail so the tool understands what i actually need instead of just saying give me gift ideas under 30 dollars i should say give me five ideas for a 29 year old who loves winter sports and recently switched from snowboarding to skiing

References are examples i give the ai to work off of like showing past gifts ive given so it understands my taste better not every prompt will have clear references specially if the task is abstract or im just looking for inspiration

Evaluate means checking if the output actually gave me what i needed and iterate means refining the prompt if it didnt order of these steps doesnt matter as much as just making sure the substance is there

## Human in the loop

No matter how good the ai tool is it still needs human involvement because it doesnt have the real world experience and judgement we have this is called human in the loop and it means combining machine and human intelligence to train use verify and refine ai results

Before using ai i should always think about whether im entering sensitive or confidential info and check my organizations policy first same goes even outside work always check how the data i enter might get used

## Using ai to understand security frameworks

Frameworks like NIST 800-53 are massive like 492 pages so digging through them manually for a specific control is time consuming ai can help explain complex controls quickly

Example prompt style would be something like introducing myself as a security analyst asking about a specific control like SI-5 what it requires how to implement it and what enhancements are worth adopting given that im not building a federal system so enhancements are optional not mandatory this context part matters because it tells the tool the enhancements arent strict requirements

If the explanation is still confusing i can ask it to explain like im new to the field or even explain it like im in elementary school or ask for analogies metaphors or real world examples until it clicks

## Using ai to debug and improve code

Ai tools like gemini can act as a code reviewer i can just paste in python code and ask what bugs if any exist for example a zero division error can happen if the code divides todays login count by average logins per day and that average happens to be zero like for a new employee gemini can catch this and suggest adding a conditional check so the error is handled gracefully instead of breaking the code

When debugging code less context is actually better since code is precise and structured too much extra info can distract the ai from the actual issue this is different from most other prompts where more context usually helps

Ai can also help improve and comment existing code especially if i inherited someone elses script with no comments i can ask it to add comments explaining each section and suggest ways to improve it it can also help write code completely from scratch not just fix existing stuff

## Using ai to learn about vulnerabilities

I can ask gemini to define specific vulnerabilities like server side request forgery injection cryptographic failures and broken access control along with their impact and mitigation steps adding context like saying im a junior analyst new to the field helps tailor the response to my level

If the mitigation steps feel too short i go back into iterate mode by asking for more detail giving examples of what im expecting or breaking my questions into shorter clearer prompts asking why repeatedly also helps dig into root causes

Bonus tip is i can also ask gemini for sample interview questions about vulnerabilities practice answering them myself then compare with what gemini says

## Using ai for detection and response

For incident response i can paste alert details and ask gemini to help prioritize them based on severity and potential impact it gives back a prioritized list with reasoning and sometimes flags extra things to consider like checking if multiple alerts are connected for example a SYN flood could be a diversion tactic for something bigger

My incident response plan should always be the first thing i check but if a scenario isnt covered in it ai can help me figure out next steps and even help me update the plan afterward so its more complete next time

## Responsible use guidelines

Basic rules for using ai responsibly

- review outputs carefully for accuracy
- disclose that ai was used
- avoid entering sensitive or private info
- always keep a human in the loop since ai should complement not replace human judgement