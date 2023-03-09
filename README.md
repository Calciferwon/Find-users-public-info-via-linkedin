# Find users'public info via linkedin

Introduction
1. Preface

At AhaSlides.

Recently, when I realized that Enterprises are the highest potential users who are both tend to fully adopt our products and like to pay more then we know that our marketing strategies should be adjusted.

However, before thinking of any new marketing ideas we firstly need to understand our Enterprise users. At least, we have to be aware of who they are and how they use our products. Actually we don't know enough. Our data provides us with wonderful users' behavior but that's all.
We are urgent to build user personas that shape our strategies in the next few years of developing our products.

At that moment, I did give myself a question. Why couldn't us enrich our data to help marketing team build up user personas? Why cann't us find data from other sources to have a better understanding on our users?

Linkedin, for that reason, is the best answer for my questions.

On linkedIn, people show up  full of professional experience such as current employers, titles, experiences and their career path. This information is very precious to learn more about them. That's all what we need. Now, the next action should be finding a way to collect information from linkedIn via users' emails

Nevertheless, linkedIn is not a public warehouse that we can get in and take any thing out free or charge. This platform does not share its users' information easily and owns a great wall preventing all effort to crawl data.

How can we collect data from linkedIn with the lowest price? That is a big question to answer

After searching for solutions, I found out that we can use serper.dev, a product of Paddle.com

This platform provides us a SERP api to make mass search on google with very affordable prices (As the image below)

![image](https://user-images.githubusercontent.com/88567721/224064752-a32acbce-0e83-423a-b565-ea1f6b811e17.png)

Besides, Mixpanel also works as the Database where we take users' email out and store information from linkedIn. That is the reason why, in this context, we will work a lot with Mixpanel APIs.
Actually, our Datawarehouse is on Amazon S3 however Mixpanel gives us really convenient user interface for marketing team to work with and powerful storage system

2. Methodology
Data workflow:
Mixpanel -> serper.dev -> Mixpanel

2.1. Mixpanel to serper.dev
- From Mixpanel, User profile are extracted with 2 columns: userId and email
- Users' email will be looked up on google via SEPR api provided by serper.dev to find if is there any linkedIn profile linked
- If yes, serper.dev will return the summary of this linkedIn profile including full name, company and professional title

2.2. Serper.dev to Mixpanel
- All lookup information from linkedIn will be match with users profiles from Mixpanel corresponding to emails & userId
- This data is packed to a Dataframe before returning to Mixpanel
- Use Mixpanel API to update users' profiles

3. Scope of work
We all know that people submit a lot of other information to linkedIn for the work purpose such as: personal infor, skills, work experiences, ... Nonetheless, I currently collect only people full name, company name & title that would be great for me to build up user personas (along with available data on my Database). This info can be easily provided by serper.dev through looking up users' emails.
In the future, more infor would be considered to collect if needed
