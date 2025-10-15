# Demand-Forecast

Note: The model for forecasting is in the demand forecast notebook; the Read Me your reading dwells into the EDA or analysis part.

# Content
1. [Impact of promotions](Analyzing Promotional effect)


## Analyzing Promotional effect

The dataset was from an old Kaggle competition(Rossmann store sales data), and its data has enough to create a forecasting model, but no customer info. So I had to do with what I had.

The key questions I wanted to answer were:
1. Did promotions impact sales on average? Was it worth it?
2. How can I quantify the effect of the promo?

With relevant data only having the number of stores, sales, and when they conducted a promo. I had to deal with available data.

What steps did I take?

1. Checking how the store operated.

2. When is the promo in effect ( Day of Week)

3. Calculate Lift%

4. Statistical test to confirm its significance and that it’s not by chance.

### How the store operates:
The stores ( there are 1000 stores from Germany) are open Mon - Sat, and most stores are closed on Sundays, with some exceptions.
<img width="807" height="524" alt="promo1" src="https://github.com/user-attachments/assets/a0d0aab9-0043-43ad-abae-cd2e0a3dc586" />



The promo is always conducted Mon-Fri without exception. There have never been promotions on weekends, only on weekdays.
<img width="807" height="524" alt="promo2" src="https://github.com/user-attachments/assets/c51c186c-995a-4b7b-9f14-a96002476747" />



When comparing Sales when the promo was running and when it was not can be tricky since stores are normally closed on Sundays and the promo is not done on weekends. When we plot the sales distribution by promo, we can be misled since it will show stores with no promo have 25% zero sales in the distribution.
<img width="807" height="524" alt="promo - sales distri" src="https://github.com/user-attachments/assets/e2502706-efc3-4a5e-ab02-db4988e2cbaa" />



### Calculating the Effect of Promo (Lift %):
Lift (%) measures how much sales increased during promotions compared to normal days.

The lift formula goes like this:

Lift (%) = ((Average Sales during Promotion − Average Sales without Promotion) / Average Sales without Promotion) × 100

We can visualize the effect by plotting lift with stores.
<img width="807" height="524" alt="promo - lift distri" src="https://github.com/user-attachments/assets/9016f5fd-5a21-4e4e-874c-61f17bf3b421" />


We can see that a high number of stores do benefit from promotions, and most stores have a 40-90% lift.

### Confirming our assumption, Statistically:
We can use a simple hypothesis test to confirm it.

For large data, we can assume normality and use a t-test or use non-parametric tests like the Mann-Whitney U test.

For your information, the data set is indeed not normal, and we can see it when we plot a QQ plot.
<img width="1768" height="1361" alt="promo qq" src="https://github.com/user-attachments/assets/2f53a7af-a767-41a8-8c1e-a34a10c7fac9" />


There is a cluster at 0, which is when the store is closed. Even when log-transformed, the cluster exists. Hence, I conducted both a t-test and a Mann-Whitney U test. Both resulted in a strong significance that there was a high impact of conducting promotions.

