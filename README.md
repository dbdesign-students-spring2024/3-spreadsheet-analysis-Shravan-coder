# Spreadsheet Analysis

## Data Set Report

### Data Origin

The data I am analyzing is the total annual mechandise exports by every country between the years 2017 and 2022. The data is divided by product group, with separate divisions for things like Agricultural Products, Manufactures, Chemicals, etc. I got this data directly from the WTO (World Trade Organization)'s website. The URL is provided below. I downloaded the data in CSV format.

https://stats.wto.org/?idSavedQuery=fbed72d4-6b98-4cbb-a6b5-7bea672a561a

### Munging the Data

The first thing I did was to shorten the "Product/Sector" column to only contain the names of the product sectors and not the weird codes the WTO uses to classify them. This was done without major issue.

I also deleted the column "Partner Economy". The column referred to the trading partner which the Reporting Economy (country) was exporting to, and in the vast majority of cases it was the world. I presumed the reader would take the fact that every country exports to the rest of the world as a given and deleted the column. The only Reporting Economy who's trading partner was not the world was the EU, which I dealt with next.

There were many non-countries that were registered as "Reporting Economies" in the data set. many of these non-countries were international organizations made up of countries on the list, such as ASEAN, the EU, BRICS, and others were simply continents like Asia and North America. If I were to include these rows in my data set, I would be double counting many countries. Therefore, I decided to get rid of them.

To get rid of every single non-country, I found a dictionary of every single country online and put it in munge.py. If a Reporting Economy was not on said list, I excluded it from the data set. This was a particularly annoying task, as I had to make sure the countries names in the data set and my dictionary matched. The WTO bizzarely decided to use the official names for seemingly random countries such as the "Lebanese Republic" instead of Lebanon, and the "Lao People's Democratic Republic" instead of Laos. Ensuring that no actual country was left out took a while.

I deleted the row for each country which showed the sum of all their exports for every year. I could calculate it through Excel functions regardless, and the existence of the row hindered my ability to find the max quantity of any product group exported by any country. Furthermore, excluding it when summing up total exports for any given year would make my Excel functions needlessly complicated, so I chose to get rid of the rows and recalculate them in Excel if necessary.

I also got rid of all the rows counting "fuel" and "food" in an economy, as those were already counted by the "Agricultural products" and "Fuel and mining equipment" categories. I may be double counting in other categories however, as I do not know exactly what goes into each category.

## Data Analysis

### Aggregate Statistics Analysis

The first 2 stats show the total world exports in 2019 and 2020. The total amount of exports from every country in 2019 is around 3.6 * 10^14 USD, and in 2020 its 3.3 * 10^14 USD. Usually, global exports have increased year on year - however, this drop in global exports in indicative of the effect the COVID-19 pandemic had on the global trade, reducing it significantly. I was surprised the drop wasn't a larger fraction of total exports - however, evaluating the number on it's own (3 * 10^13 USD lost), we can see how significant the impact truly was.

The next 2 statistics find the largest single export of any single country to the rest of the world in 2017 and 2022. Unsurprisingly, both times the largest export was China's manufactures. China's economic growth was spurred by it's manufacturing sector - it used various techniques, such as artificially keeping the exchange rate of the rmb low, to accelerate the sector. Here we see the results - China's manufacturing has emerged as it's main export. Comparing it to total exports in 2019 and 2020, even though the total exports for 2017 and 2022 aren't *exactly* the same, it's still aparent that Chinese manufacturing exports make up a significant portion of the world's total exports.

### Aggregate Statistics with Conditions Analysis

I then calculated the average agricultural export per country in 2022, which was 13981 million USD, and the average manufacturing export per country in 2022, which is 95726 million USD. What's apparent here is the difference in the value of agricultural and manufacturing exports - the former is only a fraction of the latter. This idea underpins a notable concept of the economic development of countries: that a country can become prosperous through manufacturing exports rather than exporting agricultural products. Many Asian nations, such as South Korea, Japan, and the aforementioned China, have used this idea to attain sky high GDP growth rates, whereas most agrarian nations lack the same economic prosperity.

I then found the country with the max agricultural exports in 2022, which was the USA at 222163 million USD. While agricultural exports are not necessarily indicators of economic growth (agriculture is not even in the US's top 3 exports), it is a valuable indicator of geopolitical power. As shown through the grain deficiency during the onset of the Russia-Ukraine War, agricultural imports are important for many countries very survival. The US's agricultural exports are indicative of the influence they have in these markets, and therefore, the influence the country wields.

### Chart Analysis

My final chart includes a line graph total world exports per year. The y axis is exports in millions of USD and the x axis is years since 2016. As has been shown by some of my statistics, we can see the total exports per year slowly increasing before experiencing a slight dip during 2019 and 2020 before getting back on track. The 2020 dip can be explained by COVID-19, and the 2019 dip can be in part explained by the US-China trade war that happened at the time. However, the general trend for global exports is slow upwards growth.

## Extra Credit

I believe this assignment deserve extra credit due to my sample data set being over 2400 rows long, thus fulfilling the conditions for a large data set of thousands of rows.
