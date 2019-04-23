# Approach To Deal With Overdraw

Presentation Slides [\[link\]](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/approach_to_deal_with_overdraw.pdf)

## Video

TBA

## Slides

![01](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_01.jpeg)

Hi everyone, my name is Brian, a second year Computer Science Master Student.
Today, I am going to talk about “Approach To Deal With Overdraw”.

![02](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_02.jpeg)

Here is today’s agenda.
Before we jump into the topic, I would like to show you some examples of overdraw.

![03](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_03.jpeg)

Overdraw refers to overlapping points or overplotting.
Here is an example of overdraw from our previous homework.
You would be able to tell from the picture that there are tons of data points on the map but.
Now, if I ask you which part of the map contains more data, you may assume that there might be more records in the upper-right corner.

![04](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_04.jpeg)

However, there are actually more records in the middle.
You can hardly tell until I show you a visualization with different encoding.

![05](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_05.jpeg)

Here is another example.
Can you tell me how many data points in both circles?
It’s actually more than what you think.

![06](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_06.jpeg)

You would be able to see the reason in Tableau.
There were actually 10 orange points overlapping with each other.

![07](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_07.jpeg)

So, the first motivation of this talk is that scatterplots or scatterplot matrices are commonly used and overdraw is one of the major problem in those techniques.
Although the examples I showed you were not scatterplots, they do have some similarities.
Furthermore, overdraw did happen in our previous homework.
Which is why I think you would be benefited from this talk to reduce the lying factors in your visualizations.

![08](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_08.jpeg)

My topic was built on the paper “Using Animation to Alleviate Overdraw in Multiclass Scatterplot Matrices”,
which I am going to refer as SPLOMs during this talk.
The paper was written by our Professor Sophie Engle last year.
It explores whether animation using flickering points is an effective way to alleviate overdraw.

![09](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_09.jpeg)

For the background of Multiclass SPLOM, it’s basically a grid of scatterplots.
Each scatterplot is encoding with two variables based on its column and row positions.
For example, this one in the upper-left corner is a scatterplot in column Z and row V.
In this particular plot, it is encoding Z values with horizontal position and V values with vertical position.
The color encoding is based on some kind of class or category.

![10](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_10.jpeg)

So why did the paper focus on Multiclass SPLOMs?
One of the major problems with visualizing scatterplots or SPLOMs is with overdraw for moderate to large datasets.
On the other hand, scatterplots have been actively researched while multiclass SPLOM is one of the hardest and least studied setting for alleviating overdraw.
Moreover, common plotting techniques don’t really work on this specific setting.
Here is a graph of common plotting techniques, you can see how badly they perform when there is overdraw.

![11](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_11.jpeg)

The approach in the paper continuously redraws data points.
So new data would be above the old ones which allows us to see every data point throughout the time.
I do want to point out that this is not presenting the change of the data overtime.
The approach works the best in the dense regions.
Like here we have many movements indicates that we have many points but not many different classes.
Here we have a dense region with many points and many classes.
One of the nice things with this approach is that it does support interactivity like highlighting.
So you can unselect the classes you don’t want to observe and they will turn gray.

![12](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_12.jpeg)

One question came up during the research: does this kind of animation actually distract the audience?
So they did the user study with 69 participants and 33% of them were females.
The study recruited students from Data Visualization class directly.
Therefore, 78% of them were between 18 and 24 years old.
And due to the fact, most of them were at least somewhat comfortable with the SPLOM techniques.
Here I am going to do a live demo.

I’ve installed the [Experimentr](https://github.com/codementum/experimentr) framework which is the exact framework they used to do the user study.
The framework first collects the demographic data from the user and it shows the instructions regarding how to interact with it.
Then the study split into two tasks, one is targeted density, that the framework will ask the user to drag a rectangle into a very specific plot that has the most data points.
The other one is diverse density, which the framework won’t indicate a specific plot.
The framework uses both static and animated SPLOMs.
Therefore, they can study whether the users can better identify the region with the most data point when using static or animated techniques.

![13](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_13.jpeg)

It turned out that the animated SPLOMs did outperform static ones for both targeted and diverse density tasks.
About 77% of the participants preferred animated SPLOMs.
On the other hand, 30% of the participants found animation was distracting.
And surprisingly, there were also 30% of the participants performed worse with animated SPLOMs.
So this is not for everyone.
Which is why the framework allows the you to disable the animation or adjust the speed to make it more comfortable with the user.

![14](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_14.jpeg)

For the conclusion, I found myself preferred the animated techniques.
But with one condition: I need more time to observe the animated SPLOMs compare to the static ones.
In average, I used about 4 seconds to observe each region in animated SPLOMs while it only took me about 2 to 3 seconds to go through each region in the static ones.
Nevertheless, I would choose to spend more time on actually understanding the data instead of being lied by the overdraw.
And I hope we would adopt a similar approach to deal with the overdraw problem in the further.

![15](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_15.jpeg)

Thank you very much!
Is there any question?

Why don’t we do something like sampling or filtering?
Those approaches might make the dataset less representative and you might lose some outliers.
Sometimes, those outliers make the whole story more attractive.

![16](https://raw.githubusercontent.com/ohbriansung/data_visualization_talk/master/img/data_vis_talk_16.jpeg)

I do want to encourage you to play with the website and here is the [link](http://vgl.cs.usfca.edu/animated-sploms/).
If you need to review the content of this presentation, you can find the slides on my website.
