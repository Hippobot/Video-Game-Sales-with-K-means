# Video-Game-Sales-with-K-means
This project aims to use K means with PCA to analyze and make sense of 16,000+ data entries that correspond to video game sales. The data shows the name of the video game and its corresponding console, the game’s publisher, sales across regions, and the game’s ratings.

Section 0 - Introduce the problem

The landscape of video games is changing rapidly, with technological improvements seemingly occurring every year. In addition to the perceived improvements, video games are now more expensive and reviewing video games has become a major sector. After being burned out on pre-ordering games, I and some of my friends now wait for the game to launch in order to read/watch reviews in order to make an informed purchase. I plan to visualize and cluster the data so as to find patterns that contribute to video game sales. I will specifically be looking at 'Average_Score' as my main target variable.

Additional questions that I plan to answer include:

What game region has sold the most? This is important as it helps to showcase the differences in sales across regions.

What game has the highest rating? Also important in how you view the highest rated game from the realm of critic/user reviews.

Does the highest critic rating have the highest user rating as well? To showcase the relationship between critic and user ratings.

Which console system has sold the most? Also show how other systems compare. This can be used to showcase which console contributed to the highest video game sales.

Show the most popular video game genres. A fun metric to look at.

Section 1 - What is Clustering?
![Screenshot 2024-09-24 155335](https://github.com/user-attachments/assets/932af5fe-019f-4eb3-9092-6f7c65aaa821)

Clustering is the process of finding subgroups in data in the form of clusters in order to find homogeneous subgroups within the data. K-means is a method of vector quantization and is a form of unsupervised learning to find patterns without prior knowledge. In addition to K-means I will use PCA. PCA is known as principal component analysis which is a technique used for dimensionality reduction that also aims to preserve as much of the data's variability as possible.

Section 2 - Data

My data set comes from Kaggle, and I based it on one of my interests. The data set shows video
game sales and ratings across a period. The data spans from the year 1985 to 2016. The dataset includes the year the video game released, sales in North America, sales in Europe, sales in Japan, Other Sales (minor regions), Global sales, critic scores, user scores, critic count, and user count. I chose this dataset because I would consider myself a person that plays video games regularly. It is a hobby of mine and it would be interesting to delve into the data directly to view how the variables interact with each other. I will be using every variable when it comes to analyzing the data to better showcase the relationships between the variables. The relationships that I am particularly paying attention to will be shown in the questions section below. 

https://www.kaggle.com/datasets/ibriiee/video-games-sales-dataset-2022-updated-extra-feat

Section 3 – Preprocessing the Data and Methodology

The bulk of the preprocessing involved cleaning the data from null values. I dropped the rows
with null values as they were more likely to be obscure games that had little to no impact on
what I was trying to answer. The null values all came from the rating side of the dataset. I also
had to create two new columns for data analysis. The first column I created was a new
“Adjusted_User_Score” that changed the score from a 10-point scale to a 100-point scale. This
was done to match the critic score. I also created an “Average_Score” column that averages out
user and critic scores to see the impact on my findings. There was a slight issue when pursuing
these newly added columns. The data types for user score and critic scores were different from
one another. In turn, I had to convert both columns to float in order to create the new
“Average_Scores” column. More preprocessing was done, which can be seen in the code
comments. The code and its comments also highlights my methodology when it comes to
approaching the video game dataset.

Section 4 – Data Understanding and Visualization

Correlation between Average Scores and Global Sales (Fig 1)

Sales Across Regions (Fig 2)

Total Video Game Sales for Every Year (Fig 3)

Top 10 Platforms from 2007 to 2016 (Fig 4)

Top 10 Platforms from 1985 to 2016 (Fig 5)

Top 10 Video Game Genres (Fig 6)

![Screenshot 2024-09-24 155410](https://github.com/user-attachments/assets/2314573f-3999-43ac-a5d6-eb522f002c28)

(Fig 1) This shows that video game ratings whether by critic or user do largely affect video game sales. Average Score and Global Sales were used in this figure.

![Screenshot 2024-09-24 155444](https://github.com/user-attachments/assets/51a5cfc1-09c1-445f-a213-7422413156b2)

(Fig 2) This shows how all the main regions compare when it comes to video game sales. If you take global sales out, one would see that the U.S dominates the video game market.

![Screenshot 2024-09-24 155503](https://github.com/user-attachments/assets/6b6c4ae0-24be-48a8-821e-af86ea9523b6)

(Fig 3) A simple figure showcasing the video game sales by year. 2007-2008 were the highest.

![Screenshot 2024-09-24 155519](https://github.com/user-attachments/assets/d43da510-0711-4991-8446-a15842643bdd)

(Fig 4) A simple figure showcasing the top 10 platforms from 2007 to 2016. The PS3 and XBOX360 dominate in popularity which is further helped by the number of popular games each system holds.

![Screenshot 2024-09-24 155532](https://github.com/user-attachments/assets/8871ae56-442a-4ef2-8942-cc7570b62570)

(Fig 5) Similar to the figure above but includes the entire dataset year range.

![Screenshot 2024-09-24 155543](https://github.com/user-attachments/assets/5efae6f2-259a-481c-af16-d767524d4ad7)

(Fig 6) A fun figure to showcase how dominating the action genre is in video games. This is very similar to the trends one can see within cinema.

![Screenshot 2024-09-24 155558](https://github.com/user-attachments/assets/ff3c3716-1d90-405c-aa48-9d156b16df59)

In addition, I was able to create tables that showcased the following:

- The highest-rated game of all time (Metacritic). (Fig 7)

- Highest-rated game based on Adjusted_User_Score. (Fig 8)

- Highest-rated game based on Adjusted_User_Score but with 50 user count or
more. (Fig 9)

- Highest-rated game based on Average_Score. (Fig 10)

- Checking the top 20 most-sold games from 2007 to 2016. (Fig 11)

![Screenshot 2024-09-24 155558](https://github.com/user-attachments/assets/6ccd738e-d862-4e83-bf57-95f74b2ad716)

(Fig 7) The highest rated game based on critic scores. Pay attention to the low critic count here, this likely influenced the critics score.

![Screenshot 2024-09-24 155736](https://github.com/user-attachments/assets/49e3dfe0-47f8-4433-bb4c-361b25c815b9)

(Fig 8) The highest rated game based on user scores. Pay attention to the low user count here, this likely influenced the user score. So in turn this is where I decided to filter the user score so that the highest rated user score would atleast have a user count of 200 or greater.

![Screenshot 2024-09-24 155759](https://github.com/user-attachments/assets/3dd7cb04-e423-4677-8789-032b74f59b77)

(Fig 9) Once filtered one can see that the game changed and the user count is now 767. This is more accurate as there are more data points here.

![Screenshot 2024-09-24 155812](https://github.com/user-attachments/assets/a293dd49-512b-4271-a6a8-d9b26a5d9c5e)

(Fig 10) This is the highest rated game based on average score. Average score takes critic and user score into consideration. 

![Screenshot 2024-09-24 155825](https://github.com/user-attachments/assets/0fdc4330-d625-4d47-bafe-22d0d9aedfc2)

(Fig 11) The best selling games from 2007 to 2016. You can see the Wii dominating the charts here while the wii is not as popular in the platform figure (figure 4&5) This is because the Wii has a smaller catalogue of games especially when it comes to multi platform. While the Wii does have a solid amount of games in the figure above. It does not show the whole picture. You can also see here a fair amount of PS3 and Xbox360 representation here.

Section 5 - Modeling and Clustering

Before I started modeling, I went ahead and created a somewhat bloated correlation matrix. Despite the bloat, I still was able to gleam some important information. 

For the correlation matrix there is plenty of correlation to go around. In focusing on the one hot encoded variables, we can see that platform choice can often correlate to certain ratings as well as certain genres. The ratings can correlate with each other. Sales also correlate heavily so I will be removing some of the sales such as global sales from the cluster modeling. I'll also be removing user score and and adjusted user score since I'll be focusing on average score when it comes to the ratings.

Now onto the modeling section the code for that can be seen below:

![Screenshot 2024-09-24 155907](https://github.com/user-attachments/assets/9690b551-4a92-4051-bb4a-c37a74172cf7)

As I've stated, I will be using K-means but before I even begin I will go ahead and apply PCA and then merge the PCA results and 'Average_Score' for visualization. This is purely as a way to reduce dimensionality. The result of which can be seen in the two images below:

![Screenshot 2024-09-24 155937](https://github.com/user-attachments/assets/d1f96358-3f6e-4876-8f39-86a68e6d95a1)

Afterwards I went ahead and used the elbow method to find the optimal number of clusters. The result of which can be seen below:

![Screenshot 2024-09-24 155950](https://github.com/user-attachments/assets/b0db42de-d18c-4947-8024-269466440701)

This is a relatively straight line but you can slightly see that after k=3 the drop is lower so I went ahead and used k=3 going forward. Afterwards I went ahead and visualized my clusters and also used plotly which is an interactive plot that you can use with the code file that is linked at the top of this page.

![image](https://github.com/user-attachments/assets/0a260c0f-fec9-4703-a180-25a1507f0118)

![image](https://github.com/user-attachments/assets/4df1fac1-a3e4-42a4-8cbb-f360114a2f7e)

Section 6 - Storytelling and Analysis

We learned many things from the video game sales/ratings dataset. For starters, 2007-2008 had the highest video game sales. The US region dwarfs the other areas in terms of video game sales. There is a correlation between video game scores and global video game sales, this is purely seen in the visualization section. The trend shows that as the score increases, so does the likelihood of achieving more video game sales. We learned what the highest-rated games were based on critic, user, and average scores. Based on critic scores, "Tony Hawk's Pro Skater 2" is the most critically acclaimed. Based on user and average scores, "Resident Evil 4" and "Metroid Prime" were the highest respectively. We also found which platforms dominated in terms of sales. We were able to do this for all the years of the data set. This showed that video game platforms lost support and shrunk in sales percentage over time. The Xbox 360 and Wii sold the most games from 1985 and 2016. And finally, to no surprise, we learned that the action genre is the most popular video game genre. This largely mimics cinema as adventure and action also seem to dominate the box office.

When it came to clustering, I couldn't find any clear patterns when it came to Average_Score as there is a wide range of overlap and no clear patterns are present. This suggests that average score is not a significant enough metric that influences video games sales, etc. These findings also line up with existing research that suggests that video game reviews do not significantly impact sales in any meaningful way. That is unless a video game reviews extremely poorly.

Section 7: Impact
In terms of impact, this project has low impact. The project is meant to educate and not to base
decisions on. If there would be impact, it would be in considering video game scores in terms of
sales. Since there is correlation between both variables, video game publishes/studios could push
for better scores in order to influence their sales. This has been seen in the industry where
publishers will punish studios who do not meet certain Metacritic scores. Yet there is existing
data that shows that this might not always be the case and that good reviews while great do not
fully influence game sales.

References:
https://arstechnica.com/gaming/2014/04/steam-gauge-do-strong-reviews-lead-to-stronger-saleson-steam/
https://www.statista.com/statistics/188658/movie-genres-in-north-america-by-box-officerevenue-since-1995/
https://nycdatascience.com/blog/student-works/data-trends-in-video-game-sales-and-ratings/
https://www.kaggle.com/datasets/ibriiee/video-games-sales-dataset-2022-updated-extra-feat
https://www.techdirt.com/2016/12/13/game-review-site-says-square-enix-blacklisted-them-topunish-low-review-scoreshttps://https://www.towardsdatascience.com/k-means-clustering-algorithm-applications-evaluation-methods-and-drawbacks-aa03e644b48a
