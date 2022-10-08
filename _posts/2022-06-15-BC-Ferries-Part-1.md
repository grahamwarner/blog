## BC Ferries - Part 1

![Image of ferry](/grahamwarner/images/ferry_landscape.jpg)

### Project Introduction

I live on Vancouver Island and occasionally travel from Swartz Bay to Tsawwassen via [BC Ferries](https://www.bcferries.com), usually with my car. The ferries on this route run every 1-2 hours and can get full during busy times so you might need to wait a sailing (or more) if you're unlucky. You can drive to the terminal and purchase a ticket with the hopes that there will be space available, or you can purchase a reservation ($17.00 at time of writing) to reserve your spot. You can purchase reservations up to the day before sailing, as long as the reservations haven't sold out. In order to claim your reservation, you must arrive at the terminal between 30 and 60 minutes before the scheduled sailing time. Your reservation is void if you show up less than 30 minutes before sailing.

There are 2 situations to avoid:
1. Arriving at the ferry terminal just after the ferry becomes full. This is frustrating because you may have to wait 1+ hours for the next ferry, and had you arrived slightly earlier, you might have saved yourself hours of wait time.
2. Paying for a reservation and then finding the ferry empty once you get to the terminal.

It can take several minutes to get through the ticketing lineup, so if you purchase a reservation you would likely aim to arrive at the terminal ~40 minutes before sailing (assuming <10 minutes in the lineup). 

There are two situations that I want to model for this project:
1. You are planning a trip well in advance and know you will be constrained by time so you will only be able to arrive at the terminal 40 minutes before sailing. You would like to know if your planned sailing will be full so you can decide if you need to purchase a reservation. If the sailing won't be full, there is no need to waste money on a reservation.
2. You are trying to get on a particular sailing but haven't purchased a reservation. You have flexibility in how early you can arrive at the terminal so you want to know at what time the ferry will become full. Your strategy might be to arrive at the terminal 10 minutes before the sailing becomes full to make sure you get on the ferry but don't waste excessive time waiting at the terminal.

### Data Collection and Exploration

In order to predict if or when a sailing is going to be full, we need to collect data on how often ferries have been full historically. The BC Ferries website shows, in real time, the free space on their sailings for the current day (and the next few sailings on the next day), but historical data is not available. For this project, I set up a script to scrape the tabular data from the BC Ferries website to build up a dataset to analyze. I focussed on the route from Swartz Bay to Tsawwassen. The [current conditions](https://www.bcferries.com/current-conditions/SWB-TSA?) for that route are updated every 5 minutes, so my web scraping script ran at the same interval and I stored the results in my own postgres database.

The current conditions site includes information such as the sailing time, ferry name, space available for future sailings (in terms of percentage overall, for the lower vehicle deck, and upper vehicle deck), and the status for in progress/completed sailings such as their arrival time or if the sailing was cancelled. Here is an example of the current conditions from 7 Oct 2022.

![](/images/current_conditions.png)

I have been collecting data since 2022-06-29 and for this analysis, will be considering data up to 2022-10-07. Here are some basic stats about the dataset I collected over this period:
* Total number of snapshots of the current conditions table: >275,000
* Total number of sailings: 1388
* Number of distinct ferries: 5

One of the most basic questions to answer regarding situation 1 is how often do you need a reservation? Out of the 1388 unique sailings, only 1268 sailings had enough data to answer this question because of missing data around reservation cutoff time while I was developing the web scraping code. Of these 1268 sailings, 365 (28.8%) were full 30 minutes before departure.

The sailings were much more likely to be full on certain days of the week. The following plot shows sailings on Sunday, Monday, and Friday were the most likely to be full. Sunday/Monday sailings were full more often from the rush of mainland residents returning home after the weekend. Friday sailings were full more often because of Vancouver Island residents visiting the mainland for the weekend.

![](/images/proportion_full_dow.png)

The sailings were much more likely to be full at certain times of the day. The following plot shows the proportion of full sailings by departure time hour. Note that some departure times (e.g., 6 am, 8 pm) were observed infrequently so the proportion estimates have large uncertainty. The 7 pm sailings were much more likely to be full than the 9 am sailings.

![](/images/proportion_full_hour.png)
