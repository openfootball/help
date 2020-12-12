# Help & Support 


## Anybody out there?

Please, note so far this is an all-volunteer-effort from a single humble nobody (or is that a lunatic?). Anyways, just imagine how much more progress there could be if you join in and help out? What an idea. 



**Big thanks to the football.db Alumnis**

_Thanks for helping with match updates! Come back soon._

[4lp](https://github.com/4lp) • 
[bjoern3](https://github.com/bjoern3) •
[Carl Svensson (cecomp64)](https://github.com/cecomp64) •
[Jose Borja (Chakaitos)](https://github.com/Chakaitos) •
[David (davidavz)](https://github.com/davidavz) •
[Dirk Gómez (dirkgomez)](https://github.com/dirkgomez) •
[Enrique Lopez Magallon (enadol)](https://github.com/enadol) •
[fchristysen](https://github.com/fchristysen) •
[Tarek Amr (gr33ndata)](https://github.com/gr33ndata) •
[Hidenobu Nagai (hidenobunagai)](https://github.com/hidenobunagai) •
[Joe K (jokecamp)](https://github.com/jokecamp) •
[Kaspi](https://github.com/Kaspi) •
[Kıvanç Çakmak (kivanccakmak)](https://github.com/kivanccakmak) •
[Lari Kovanen (larkov)](https://github.com/larkov) •
[lokomass](https://github.com/lokomass) •
[Mahdi Taghizadeh (mahdi)](https://github.com/mahdi) •
[Kevin Christopher Henry (marfire)](https://github.com/marfire) •
[mgidon](https://github.com/mgidon) •
[Michael O'Dell (mpodell)](https://github.com/mpodell) •
[Gabriele N (noso2k1)](https://github.com/noso2k1) •
[pratul-nayak](https://github.com/pratul-nayak) •
[Rafael Pereira (rlpereira)](https://github.com/rlpereira) •
[SDoehren](https://github.com/SDoehren) •
[Stevie Howard (stvhwrd)](https://github.com/stvhwrd)



## Frequently Asked Questions and Answers (FAQs)

> Note:  The FAQs are somewhat outdated, sorry (but what can I do? - see above). For now the focus is on... guess what? Yes, more automation to hand off more work to our ye good ol' friend - the computer - to get more football data updates (automagically). 


Contents:

- [Troubleshooting](#troubleshooting)
- [Download Pre-Built Copies or Build Your Own](#download-pre-built-copies-or-build-your-own)
- [Real-Time Result / Score HTTP JSON API Web Services](#real-time-result--score-http-json-api-web-services)
- [**Contribute / Update Match Scores, Schedules, Leagues**](#contribute--update-match-scores-schedules-leagues)
- [League Standings / Stats](#league-standings--stats)
- [Text Formats (Match Schedule / Player / Squads Mini Languages)](#text-formats-match-schedule--player--squads-mini-languages)
- [Export Formats (JSON, CSV, SQL)](#export-formats-json-csv-sql)
- [Apps, Apps, Apps](#apps-apps-apps)
- [Questions? Comments?](#questions-comments)



## Troubleshooting

#### Q: I'm getting a "`no match for club`" error when building an up-to-date copy using the latest datasets?

When running `sportdb build` I'm getting the following error:

    ** !!! ERROR - no match for club >Haringey Borough FC<

---

A:  Usually that means that your installed version of the [footballdb-clubs library](https://rubygems.org/gems/footballdb-clubs) 
that ships with pre-built clubs datafiles sourced from 
[`/clubs`](https://github.com/openfootball/clubs) is out-of-sync (that is, behind) and needs an update. 

You can help yourself and use up-to-date datasets using the `--clubs-dir` option.  First download a zip archive
with the latest datasets from [`/clubs`](https://github.com/openfootball/clubs).
Click on "Code -> Download ZIP" that gets you the `clubs-master.zip` archive. Now try:

    sportdb --clubs-dir ./clubs-master.zip build 

or if you are using a quick starter template use

    sportdb --clubs-dir ./clubs-master.zip new eng

and so on.


## Download Pre-Built Copies or Build Your Own

#### Q: Where can I get (download) pre-built copies e.g. `football.db`, `worldcup.db`, `england.db` etc.?

A: You can get (download) pre-built single-file SQLite databases copies (working anywhere, that is, Windows, Mac, Linux, etc.)
on the releases page. For example, find the `worldcup.db` download at the [`/world-cup` Releases](https://github.com/openfootball/world-cup/releases) page.

Note: For now only some datasets (e.g. `worldcup.db`, `england.db`, `deutschland.db` ) have pre-built database releases.



#### Q: How can I get started building my own up-to-date copy using the latest datasets?

A: The recommended quick starter way to build your own up-to-data (local) copy from the online datasets is using datafiles.
See the [`/quick-starter` repo](https://github.com/openfootball/quick-starter) for ready-to-use quick starter datafile samples. 

Let's build a copy of all world cups (from Uruguay 1930 to Russia 2018). Use the [`worldcup.rb` datafile](https://github.com/openfootball/quick-starter/blob/master/worldcup.rb). Type:

    $ sportdb new worldcup
    
This command will run the following steps:

- Step 1:  Download `worldcup.rb` Datafile (from GitHub) to your working folder as `./Datafile`
- Step 2:  Run the `sportdb build` command
  - Step 2.a:  Download all datasets listed in the `Datafile` as zip archives (from GitHub) to `./tmp`
  - Step 2.b:  Create the "empty" database, that is, table structure, indexes, etc. (schema)
  - Step 2.c:  Read in all datasets from the zip archives in `./tmp` (no need to unpack)

That's it. Now you will have a new up-to-date single-file `sport.db` SQLite database in your working folder.


<!--
See the [How to Build Your Own Copy](http://openfootball.github.io/build.html) page
to get started building your own copy. Not really a tutorial (step-by-step guide). Sorry, still the early days.
Just start and if you have questions or commentary as you go along post
them to the [forum / mailing list](http://groups.google.com/group/opensport)
maybe someone can help you out. All the best.
Good luck. Bonus: Why not write a step-by-step build guide yourself and share
it with the world?
-->

If you have questions or commentary as you go along building your own up-to-date database copies, please post
them to the [forum / mailing list](http://groups.google.com/group/opensport)
maybe someone can help you out. All the best.
Good luck. Bonus: Why not write a step-by-step build guide yourself and share
it with the world?





## Real-Time Result / Score HTTP JSON API Web Services

#### Q: Is there any HTTP JSON API service to get live scores for _[your event here]_ e.g. the World Cup 2018 in Russia, the English Premier League 2018/19, the Euro 2020, etc.?

A: `football.db` does **NOT OFFER ANY REAL-TIME LIVE** football results / scores services.

However, you can run your own HTTP JSON API web service. 
See the official [`sport.db.service`](https://github.com/sportdb/sport.db.service) starter scripts built into 
the [`sportdb` command line tool](http://sportdb.github.io/). 
Or see the [`sport.db.starter` kits](https://github.com/sportkit) in JavaScript, Go & friends to get started building your own.


<!--
or try the [example HTTP JSON API service running on Heroku](http://footballdb.herokuapp.com).
(Note: The scores get updated once a day, that is, every 24 hours.)
-->


#### Q: What's the update frequency of the datasets?

A: It's an open source (public domain) volunteer effort.
Datasets get updated when they get updated, that is, there's no schedule and no guarantee.
If you need updates today you have at least two options:

Option 1) Contribute your updates to the datasets.

Option 2) Clone the datasets and update your own private or public copies yourself.



## Contribute / Update Match Scores, Schedules, Leagues

#### Q: How can I contribute / update match scores, schedules, leagues, etc.?


**A: (Update 2020) The recommended way to contribute football match datasets is using comma-separated values (CSV) datafiles.
See the [football.csv org](https://github.com/footballcsv) for some examples to get started today!**

<details>
   <summary>Out-of-date / Historic</summary>
A: Your contributions are welcome.
It works like a wiki, that is, the datasets are plain text documents that anybody can update
(if you're an openfootball team member - you can update it directly in your browser or push your commits;
otherwise you may use a pull request).

For example, to add the result for the Brazil vs Croatia match:

```
Thu Jun/12 17:00   Brazil  vs  Croatia
```

change the line to:

```
Thu Jun/12 17:00   Brazil  3-1 (1-1)  Croatia
```

Bonus: Let's add the goal getters too. Example:

```
Thu Jun/12 17:00   Brazil  3-1 (1-1)  Croatia
                     [Neymar 29', 71' (pen.) Oscar 90+1';  Marcelo 11' (o.g.)]
```

That's it.
</details>


## League Standings / Stats

#### Q: How can I add league standings / tables (e.g. number of matches played, won-drawn-lost, goals scored, etc.)?

A: That's the big plus using structured data. You can (auto-)calculate
league standings using SQL queries and updates.
Another big plus: Your standings will be always up-to-date (just recalculate - if out-of-date).

Note, you can use the built-in sportdb standing calculations. Still early and rough.
For auto-calculating all league standings use, for example, in your build script:

```
EventStanding.recalc!   # and for all groups
GroupStanding.recalc!
```

You can see the calc "engine" code here [\[1\]](https://github.com/sportdb/sport.db.ruby/blob/master/lib/sportdb/calc.rb).
The "engine" calculates:

- `pos` (ranking e.g. 1st place, 2nd place etc.)
- `played` (matches played)
- `won`
- `drawn`
- `lost`
- `goals_for`
- `goals_against`
- `pts` (points e.g. +3 for wins, +1 for draws etc.)


Standing tables in the sportdb schema include:

- `AlltimeStanding` / `AlltimeStandingEntry`
- `EventStanding` / `EventStandingEntry`
- `GroupStanding` / `GroupStandingEntry`

For example, using the world cup datasets you can (auto-)calculate the all time standings:

```
 1  Brazil (BRA)                 97   67  15  15  210:88   216  19
 2  Germany (GER)                99   60  19  20  206:117  199  17
 3  Italy (ITA)                  80   44  21  15  126:74   153  17
 4  Argentina (ARG)              70   37  13  20  123:80   124  15
 5  England (ENG)                59   26  19  14   77:52    97  13
 6  Spain (ESP)                  56   28  12  16   88:59    96  13
 7  France (FRA)                 54   25  11  18   96:68    86  13
 8  Netherlands (NED)            43   22  10  11   71:44    76   9
 9  Uruguay (URU)                47   18  12  17   76:65    66  11
10  Sweden (SWE)                 46   16  13  17   74:69    61  11
...
```


## Text Formats (Match Schedule / Player / Squads Mini Languages)

#### Q: What kind of text format are you using? Why not use CSV, JSON, or _[your data format here]_?

A: Most `football.db` documents use "standard" plain text formats such as
comma-separated values or key-value pairs with some exceptions.

The match schedules use a mini structured data language. Example:

```
Group A    |  Brazil    Croatia       Mexico     Cameroon
Group B    |  Spain     Netherlands   Chile      Australia
...

Matchday 1 |  Thu Jun/12
Matchday 2 |  Fri Jun/13
...

Group A:

(1) Thu Jun/12 17:00   Brazil  3-1 (1-1)  Croatia    @ Arena de São Paulo, São Paulo
                        [Neymar 29', 71' (pen.) Oscar 90+1'; Marcelo 11' (o.g.)]
...

Final

(64) Sun Jul/13 16:00  Germany  1-0 a.e.t. (0-0, 0-0)  Argentina  @ Estádio do Maracanã, Rio de Janeiro
                        [Mario Götze 113']
```


The player documents use a mini structured data language. Example:

```
Júlio César|Júlio César SOARES DE ESPINDOLA,     3 Sep 1979, 186
T. Silva|Thiago SILVA|Thiago EMILIANO DA SILVA, 22 Sep 1984, 183
David Luiz|David Luiz MOREIRA MARINHO,          22 Apr 1987, 189
Marcelo|Marcelo VIEIRA DA SILVA JUNIOR,         12 May 1988, 174
Dante|Dante BONFIM COSTA SANTOS,                18 Oct 1983, 188
```


The squads / lineups documents use a mini structured data language. Example:

```
(12)  GK  Júlio César           #  79, Toronto (CAN)
 (3)  DF  Thiago Silva          #  45, Paris Saint-Germain (FRA)
 (4)  DF  David Luiz            #  35, Chelsea (ENG)
 (6)  DF  Marcelo               #  30, Real Madrid (ESP)
(13)  DF  Dante                 #  12, Bayern Munich (GER)
```

Bonus Exercise: Try to write by hand the schedule for the English Premier League -
week-by-week - 380 matches all together, for example?
Are you enjoying writing the match schedule in JSON? in CSV? in XML? in _[your data format here]_?
Why not post an example (e.g. a link to a gist or to your document)
to the [forum / mailing list](http://groups.google.com/group/opensport) for comparison?

Now retry the exercise using the new mini language designed for making
hand-crafting schedules as easy as possible. Any difference?



#### Q: Why? Why? Why?

A: The dataset sources are plain old text documents designed to be easy-to-read and easy-to-write.
The idea is to make it work like a wiki, that is, just plain old text documents anyone can update.

Why like a wiki?

Question - What's the best source for open "unstructured" football information in the real world in 2018?
Of course, the Wikipedia! See, for example,
the [World Cup 2018](http://en.wikipedia.org/wiki/2018_FIFA_World_Cup) page,
the [World Cup 2018 squads](http://en.wikipedia.org/wiki/2018_FIFA_World_Cup_squads) page,
or the [World Cup 2018 Qualifiers](http://en.wikipedia.org/wiki/2018_FIFA_World_Cup_qualification) page.

Thus, the idea is - why not build on what works and build a wiki for "structured" data e.g.

- Wikipedia     - wiki w/ free-form text => mostly unstructured data
- `football.db` - wiki w/ mostly free-form text => always 100% structured data (ready for easy loading into SQL tables with a 100% data accuracy guarantee)



#### Q: What about Wikidata - Wikipedia's Data Project?

A: [Wikidata](http://www.wikidata.org) is a great initiative.
Wikidata like the `football.db` uses "license-free" data, that is, data dedicated to the public domain.

Thus, an idea (and goal) is to work on syncying the data
(from Wikidata to `football.db` and from `football.db` to Wikidata).
Still very early. If you're interested in making it happen or if you have any ideas, suggestions or insights,
say hello on the [forum / mailing list](http://groups.google.com/group/opensport).



## Export Formats (JSON, CSV, SQL)

#### Q: How can I get datasets in JSON, CSV, SQL or _[your data format here]_?

A: Get a copy of a pre-built database e.g. `football.db`, `worldcup.db` etc.
It's a single-file SQLite database (working anywhere, that is, Windows, Mac, Linux, etc.).

Option 1) No coding required. Use your SQLite tool of choice to export to CSV, JSON, SQL
or _[your data format here]_.

Option 2) Write your own (little) script (in Ruby, Python, etc.) that exports
to CSV, JSON or _[your data format here]_. - Bonus: Share your scripts with the world.

<!--
Add Example Script in Ruby
-->

Bonus:  You can find pre-built / ready-to-use (exported) datasets in JSON for various leagues in the [**`/football.json`**](https://github.com/openfootball/football.json) repo
and for the world cup in the [**`/world-cup.json`**](https://github.com/openfootball/world-cup.json) repo.

What about CSV? You can find pre-built / read-to-use (exported or cached from 3rd parties) datasets in CSV 
over at the [football.csv org »](https://github.com/footballcsv) 



#### Q: How can I get datasets in JSON, CSV or _[your data format here]_ using _[your database here]_ e.g. PostgreSQL, MySQL, etc.?

A: Load the datasets into your (SQL) database of choice e.g. PostgreSQL, MySQL, etc. and

Option 1) use your database tool of choice to export to CSV, JSON, SQL
or _[your data format here]_ etc. or

Option 2) use your language of choice and wipe up some code to export to CSV, JSON
or _[your data format here]_ etc.  - Bonus: Share your code with the world.




## Apps, Apps, Apps

#### Q: Any real world apps using this?

A: There's no API key, there's no registration, there's no license for the datasets.
You're free to use whatever you need - no questions asked, no rights reserved.
If you're using the football.db datasets in your app, you're welcome to tell the world (on the [mailing list/forum](http://groups.google.com/group/opensport))
and you get listed here:

- [Major League Soccer Almanac](http://mls-almanac.herokuapp.com) - [(Source)](https://github.com/cecomp64/mls-almanac) query-able, historical data for Major League Soccer in the US and Canada by Carl-Erik Svensson

<!--  no longer availabe?
- [BITKUP.COM](http://bitkup.com) - new app for betting with Bitcoins on the Brazil's World Cup 2014 by Oriol Franquesa Cortés
-->



## Questions? Comments?

Send them along to the
[Open Sports & Friends Forum/Mailing List](http://groups.google.com/group/opensport).
Thanks!
