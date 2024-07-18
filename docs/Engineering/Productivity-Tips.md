# Productivity Tips

Owner: Sean Teeling
Created time: January 29, 2024 3:39 PM

These core values aim to create a healthy work environment, and a well-oiled engine that executes at a steady pace. Each item is presented in no particular order.

# Leverage Asynchronous tools

We are working in a very distributed set of timezones. With that, we need to be able to work asynchronously. Always over communicate details so there is no missed information, as a misguided work set of directions and cascade into multiple days of lost time.

Leverage screen recording tools like vidyard, loom, and recordit. Don’t spend too much time trying to perfect the recording; in a live demo, we all say “um”, make mistakes, and take pauses. Crank out quick recordings and move on to the next task.

# Invest Lots of Time in Saving Time

A quick example is testing your code in AZDO pipelines. These pipelines, which build, lint, and test code, often take 20+ minutes. If it takes 30 iterations to get your code to work, you've lost 10 hours of work just on testing. In a day filled with meetings and context switching this might span 2-3 days, just on a *single* PR. With only 7 PR's you've lost a whole month of work.

Now imagine you spent 3 weeks of dev work investing in a tool that let you build, run, deploy, and test your code in less than 30s. You can run all those tests for those 7 PR's in about an hour. By spending time up front, you actually saved time, learned new skills, and built something that will continue to save you time in the future.

These types of savings compound. Time savings task can even be down to the subsecond level, like learning keyboard shortcuts for faster code navigation. Anything you do more than 10 times a day should take less than 1 minute. If not, you should budget allocating time to automate that task. See the (always) relevant xkcd:

![https://imgs.xkcd.com/comics/is_it_worth_the_time_2x.png](https://imgs.xkcd.com/comics/is_it_worth_the_time_2x.png)

# Mistakes Are Good in Moderation

We learn more from our mistakes than from our successes. Obviously, we shouldn't aim to make mistakes, but too often the goal of perfection can create an unhealthy culture where everything is scrutinized and progress grinds to a halt. We aim to strike a balance with making mistakes and ensure that we learn from them to avoid repeating them.

# Create a Blameless Culture

When mistakes are made its important to remain blameless. Is this the first time the mistake was made? If so, good, let's put guard rails in place to avoid it in the future. If not, did we conduct a postmortem the previous time? Did we identify proper mitigations to prevent it from happening?

People are going to make mistakes; software will not. Let's accept that and leverage software to prevent future errors and remove the expectation of perfection from individuals, and place the blame on the systems and processes, not the people.

# The Pareto Principle (80/20 rule)

This is one of my favorites, because I feel it is so ubiquitous in everything we do, yet so easy to forget if we don't constantly remind ourselves.

A project is never done, and that last 20% of the work not only tends to take 80% of the time, but likely has diminishing returns on value. Always aim to provide the most value with the least effort, and know when to move on to the next best "bang-for-your-buck". Similarly, 80% of the work may be completed with only 20% of the effort. Is this good enough for us to move on to the next project?

# Overhead should be proportionate to total potential effort

We equate overhead to the sum of time spent in planning and discussion. The total potential effort of a project is hard to quantify, but we equate it to the sum of:

- Time to complete the project
- Time for team to ramp up on new material
- Time spent mitigating possible outages
- Time spent reversing the project (in the case that the project as whole is deemed a mistake)
- Risk! Risk isn’t quite effort, but potential risk to customers or the service should be taken into high consideration and quantified in some way.

Planning and discussion should be a tool that is useful to us. That typically means it should be a fraction of the total potential effort. The moment we spend more time planning is the moment our team loses its productive velocity. The moment our tools, or processes become less than useful we need to reevaluate.

One example for a well-deserved large planning phase is in API design, since those are typically quite hard to revert once customers get their hands on them.

# Finding comfort in discomfort

We should always be just on the edge of discomfort. Discomfort is where we learn & grow, and we should learn to push ourselves along that boundary. It is when discomfort turns to frustration where we find an unhealthy balance. Always feel open to reach out for support if you find yourself in this scenario. Never feel afraid to ask for help.

# Tight Feedback loops and data driven decisions

Everything should be treated as an experiment. Nothing is taken for granted or accepted as optimal. As much as possible use data to quantify decisions. Microsoft Forms are an excellent way to garner feedback. Is the new meeting cadence working? Have you quantified the team's sentiment before and after setting the new meeting cadence? Has developer productivity enhanced over time? Check git history, compare against team sentiment, etc. Aim to quantify all the things.