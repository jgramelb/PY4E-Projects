Simple Python Search Spider, Page Ranker, and Visualizer

This is a set of programs that emulate some of the functions of a
search engine.  They store their data in a SQLITE3 database named
'spiderChoice.sqlite'.  This file can be removed at any time to restart the
process.

You should install the SQLite browser to view and modify
the databases from:

http://sqlitebrowser.org/

This program crawls a web site and pulls a series of pages into the
database, recording the links between pages.


http://stackoverflow.com/questions/388490/unicode-characters-in-windows-command-line-how

Mac: rm spiderChoice.sqlite
Mac: python3 spider.py

Win: del spiderChoice.sqlite
Win: spider.py

Enter web url or enter: [Enter Website Here~]
How many pages:[Enter here]

In this sample run, we told it to crawl a website and retrieve two
pages.  If you restart the program again and tell it to crawl more
pages, it will not re-crawl any pages already in the database.  Upon
restart it goes to a random non-crawled page and starts there.  So
each successive run of spiderChoice.py is additive.

You can have multiple starting points in the same database -
within the program these are called "webs".   The spider
chooses randomly amongst all non-visited links across all
the webs.

If you want to dump the contents of the spiderChoice.sqlite file, you can
run spdumpChoice.py.

This shows the number of incoming links, the old page rank, the new page
rank, the id of the page, and the url of the page.  The spdump.py program
only shows pages that have at least one incoming link to them.

Once you have a few pages in the database, you can run Page Rank on the
pages using the sprankChoice.py program.  You simply tell it how many Page
Rank iterations to run.

You can dump the database again to see that page rank has been updated:

You can run sprankChoice.py as many times as you like and it will simply refine
the page rank the more times you run it.  You can even run sprankChoice.py a few times
and then go spider a few more pages with spiderChoice.py and then run sprankChoice.py
to converge the page ranks.

If you want to restart the Page Rank calculations without re-spidering the
web pages, you can use spresetChoice.py

For each iteration of the page rank algorithm it prints the average
change per page of the page rank.   The network initially is quite
unbalanced and so the individual page ranks are changing wildly.
But in a few short iterations, the page rank converges.  You
should run sprankChoice.py long enough that the page ranks converge.

If you want to visualize the current top pages in terms of page rank,
run spjsonChoice.py to write the pages out in JSON format to be viewed in a
web browser.


Creating JSON output on spiderChoice.js...
How many nodes? 30
Open forceChoice.html in a browser to view the visualization

You can view this data by opening the file forceChoice.html in your web browser.
This shows an automatic layout of the nodes and links.  You can click and
drag any node and you can also double click on a node to find the URL
that is represented by the node.

This visualization is provided using the force layout from:

http://mbostock.github.com/d3/

If you rerun the other utilities and then re-run spjsonChoice.py - you merely
have to press refresh in the browser to get the new data from spiderChoice.js.
