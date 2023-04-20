# Actor - PaperBack Swap Scraper

## PaperBack Swap scraper

Since PaperBack Swap doesn't provide a good and free API, this actor should help you to retrieve data from it.

The PaperBack Swap data scraper supports the following features:

-   Search any keyword - Search any keyword, find the books you are looking for. Retrieve everything right away!

-   Scrape books - Name, description, ISBN numbers, prices, cover image, author, publisher any many other things are at your fingertips.

-   Get comments of any book - Get all the comments and ratings for any book.

-   Retrieve books of a certain tags - If you are looking for all the books per certain tags; you are in the right place. Just type the URL and the actor will do the rest.

-   Fetch book awards - Get all the awarded books right away!

-   Scrape books of an author - All the books that has been written by an author can be easily scraped.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/paperbackswap-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on PaperBack Swap that should be visited. Required fields are:

| Field                | Type    | Description                                                                                                                                                                                                    |
| -------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| search               | String  | (optional) Keyword that you want to search on PaperBack Swap.                                                                                                                                                       |
| includeReviews       | Boolean | (optional) This will add all the reviews that PaperBack Swap provides into the detail objects. Please keep in mind that the time and resources the actor uses will increase proportionally by the number of reviews. |
| startUrls            | Array   | (optional) List of PaperBack Swap URLs. You should only provide awards, tags, author, or book detail URLs                                                                                                                 |
| endPage              | Integer | (optional) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.                                                          |
| maxItems             | Integer | (optional) You can limit scraped items. This should be useful when you search through the big lists or search results.                                                                                                |
| proxy                | Object  | Proxy configuration                                                                                                                                                                                            |
| extendOutputFunction | String  | (optional) Function that takes a JQuery handle ($) as argument and returns object with data                                                                                                                    |
| customMapFunction | String  | (optional) Function that takes each objects handle as argument and returns object with executing the function                                                                                                                     |

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

##### Tip

When you want to have a scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detail requests. If actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.03-0.05 compute units.

### PaperBack Swap Scraper Input example

```json
{
  "startUrls":[
    "https://www.paperbackswap.com/5th-Wave-Bk-Rick-Yancey/book/0142425834/",
    "https://www.paperbackswap.com/Pulitzer-Prize/award/2/?g=History",
    "https://www.paperbackswap.com/Mark-Sanborn/author/",
    "https://www.paperbackswap.com/Christian-Fiction/tag/2043/?l=10&ls=10"
  ],
  "search":"harry potter",
  "endPage":1,
  "maxItems":10,
  "includeReviews": false,
  "proxy":{
    "useApifyProxy":true
  }
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## PaperBack Swap Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this PaperBack Swap actor.

## Scraped PaperBack Swap Properties

The structure of each item in PaperBack Swap looks like this:

### Item Detail

```json
{
	"url": "https://www.paperbackswap.com/Fantasy-Lover-Dark-Sherrilyn-Kenyon/book/0312979975/",
	"name": "Fantasy Lover",
	"subtitle": "Dark-Hunter, Bk 1",
	"description": "Dear Reader, — Being trapped in a bedroom with a woman is a grand thing. Being trapped in hundreds of bedrooms over two thousand years isn't. And being cursed into a book as a love-slave for eternity can ruin even a Spartan warrior's day. — As a love-slave, I knew everything about women. How to touch them, how to savor them, and most of al...  more »l how to pleasure them. But when I was summoned to fulfill Grace Alexander's sexual fantasies, I found the first woman in history who saw me as a man with a tormented past. She, alone, bothered to take me out of the bedroom and into the world. She taught me to love again.\n\nBut I was not born to know love. I was cursed to walk eternity alone. As a general, I had long ago accepted my sentence. Yet now I have found Grace-the one thing my wounded heart cannot survive without. Sure, love can heal all wounds, but can it break a two thousand year old curse?\n\nJulian of Macedon  « less",
	"author": {
		"name": "Sherrilyn Kenyon",
		"url": "https://www.paperbackswap.com/Sherrilyn-Kenyon/author/"
	},
	"publisher": "St. Martin's Paperbacks",
	"bookFormat": "Mass Market Paperback",
	"image": "https://nationalbookswap.com/pbs/l/73/9973/9780312979973.jpg",
	"amazonBuyLink": "https://www.amazon.com/gp/product/0312979975?SubscriptionId=AKIAJXCVBYSZT4DROVVA&tag=pbs_00005-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=0312979975",
	"isbn13": "9780312979973",
	"isbn10": "0312979975",
	"numberOfPages": "352",
	"rating": "4.2",
	"numberOfRatings": "1366",
	"highPrice": "",
	"lowPrice": "",
	"reviews": [
		{
			"author": "Rebecca H. (Goldaira)",
			"content": "I don't normally read romance novels of any kind.  I find them unbelievable and boring.  I only read this book because it was a recommendation by a friend and she dared me to read and see if I didn't like it.  I didn't like it, I loved it.  This is a fabulous book that keeps your interest.  Very enjoyable read, even for people who don't normally read this kind of stuff.  I am going to be reading more of this authors work.",
			"publishDate": "12/20/2007",
			"rating": 0
		},
	]
}
```
