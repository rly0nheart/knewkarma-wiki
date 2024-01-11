# Usage

## CLI Usage (Including the Docker Container)

After installation, the *cli* instance can be called with the `knewkarma` command (or `docker run [container-name]` for
Docker Containers)

```text
knewkarma --help
```

```text
docker run -t my-knewkarma-container --help
```
```text
Usage: knewkarma [-h] [-t {hour,day,week,month,year}]
                 [-s {controversial,new,top,best,hot,rising}] [-l NUMBER]
                 [-j FILENAME] [-c FILENAME] [-u] [-v]
                 {community,communities,posts,search,user} ...


▌ Reddit Data Analysis Toolkit.

Positional Arguments:
  {community,communities,posts,search,user}
                        operation mode
    community           community (subreddit) operations
    communities         communities (subreddits) operations
    posts               posts operations
    search              search operations
    user                user operations

Options:
  -h, --help            show this help message and exit
  -t, --timeframe {hour,day,week,month,year}
                        timeframe to get [bulk] data from (default: all)
  -s, --sort {controversial,new,top,best,hot,rising}
                        [bulk] sort criterion (default: all)
  -l, --limit NUMBER    [bulk] data output limit (default: 100)
  -j, --json FILENAME   write output to a json file
  -c, --csv FILENAME    write output to a csv file
  -u, --updates         check for updates on run
  -v, --version         show program's version number and exit
```

You can further view individual operation mode usages by calling `knewkarma` with an operation mode name and
the `-h/--help` flag.

### Community (Subreddit) Operations

```text
knewkarma community --help
```

```text
docker run -it my-knewkarma-container community --help
```
```text
Usage: knewkarma community [-h] [-p] [-s KEYWORD] [-pp] [-wp WIKI_PAGE] [-wps]
                           community


Positional Arguments:
  community             community name

Options:
  -h, --help            show this help message and exit
  -p, --profile         get a community's profile
  -s, --search KEYWORD  get a community's posts that contain the specified
                        keyword
  -pp, --posts          get a community's posts
  -wp, --wiki-page WIKI_PAGE
                        get a community's specified wiki page data
  -wps, --wiki-pages    get a community's wiki pages
```

### Communities (Subreddits) Operations
```text
knewkarma communities --help
```
```text
docker run -it my-knewkarma-container communities --help
```
```text
Usage: knewkarma communities [-h] [-a] [-d] [-n] [-p]


Options:
  -h, --help     show this help message and exit
  -a, --all      get all communities
  -d, --default  get default communities
  -n, --new      get new communities
  -p, --popular  get popular communities
```


### Posts Operations

```text
knewkarma posts --help
```

```text
docker run -it my-knewkarma-container posts --help
```
```text
Usage: knewkarma posts [-h] [-n] [-f] [-l {best,controversial,popular,rising}]


Options:
  -h, --help            show this help message and exit
  -n, --new             get new posts
  -f, --front-page      get posts from the reddit front-page
  -l, --listing {best,controversial,popular,rising}
                        get posts from a specified listing
```

### Search Operations

```text
knewkarma search --help
```

```text
docker run -it my-knewkarma-container search --help
```
```text
Usage: knewkarma search [-h] [-u] [-p] [-c] query


Positional Arguments:
  query              search query

Options:
  -h, --help         show this help message and exit
  -u, --users        search users
  -p, --posts        search posts
  -c, --communities  search communities
```

### User Operations

```text
knewkarma user --help
```

```text
docker run -it my-knewkarma-container user --help
```
```text
Usage: knewkarma user [-h] [-p] [-c] [-o] [-pp] [-sp KEYWORD] [-sc KEYWORD]
                      [-mc] [-tc TOP_N]
                      username


Positional Arguments:
  username              username

Options:
  -h, --help            show this help message and exit
  -p, --profile         get a user's profile
  -c, --comments        get a user's comments
  -o, --overview        get a user's most recent comment activity
  -pp, --posts          get a user's posts
  -sp, --search-posts KEYWORD
                        get a user's posts that contain the specified keyword
  -sc, --search-comments KEYWORD
                        get a user's comments that contain the specified
                        keyword
  -mc, --moderated-communities
                        get communities moderated by the user
  -tc, --top-communities TOP_N
                        get a user's top n communities based on community
                        frequency in n posts
```

## API Implementation & Code Examples
### User Data

```python
import asyncio
import aiohttp
from knewkarma import RedditUser

user = RedditUser(username="TheRealKSi")


# Get user's profile
async def async_profile():
    async with aiohttp.ClientSession() as session:
        profile = await user.profile(session=session)
        print(profile)


# Get user's posts
async def async_posts(limit):
    async with aiohttp.ClientSession() as session:
        # timeframes: ["hour", "day", "month", "year"]. Leave parameter unspecified to get from all timeframes.
        # sorting: ["controversial", "new", "top", "best", "hot", "rising"]. Leave parameter unspecified to get from all sort criteria.
        posts = await user.posts(limit=limit, session=session)
        print(posts)


# Get user's comments
async def async_comments(limit):
    async with aiohttp.ClientSession() as session:
        # timeframes: ["hour", "day", "month", "year"]. Leave parameter unspecified to get from all timeframes.
        # sorting: ["controversial", "new", "top", "best", "hot", "rising"]. Leave parameter unspecified to get from all sort criteria.
        comments = await user.comments(limit=limit, session=session)
        print(comments)


# Get user's most recent comment activity
async def async_overview(limit):
    async with aiohttp.ClientSession() as session:
        comments = await user.overview(limit=limit, session=session)
        print(comments)


# Get posts that contain the specified keyword
async def async_search_posts(keyword, limit):
    async with aiohttp.ClientSession() as session:
        found_posts = await user.search_posts(keyword=keyword, limit=limit, session=session)
        print(found_posts)


# Get comments that contain the specified keyword
async def async_search_comments(keyword, limit):
    async with aiohttp.ClientSession() as session:
        found_comments = await user.search_comments(keyword=keyword, limit=limit, session=session)
        print(found_comments)


# Get user's top n communities based on n post frequency
async def async_top_communities(top_n, limit):
    async with aiohttp.ClientSession() as session:
        top_communities = await user.top_communities(top_n=top_n, limit=limit, session=session)
        print(top_communities)


# Get communities moderated by user       
async def async_moderated_communities():
    async with aiohttp.ClientSession() as session:
        moderated_communities = await user.moderated_communities(session=session)
        print(moderated_communities)

# asyncio.run(async_profile())
# asyncio.run(async_posts(limit=5))
# asyncio.run(async_comments(limit=100))
# asyncio.run(async_overview(limit=50))
# asyncio.run(async_search_posts(keyword="game", limit=100))
# asyncio.run(async_search_comments(keyword="lol", limit=100))
# asyncio.run(async_top_communities(top_n=10, limit=100))
# asyncio.run(async_moderated_communities())
```

### Community (Subreddit) Data

````python
import asyncio
import aiohttp
from knewkarma import RedditCommunity

# Initialize RedditSub with the specified community
community = RedditCommunity(community="MachineLearning")


# Get a community's profile
async def async_profile():
    async with aiohttp.ClientSession() as session:
        profile = await community.profile(session=session)
        print(profile)


# Get a community's posts
async def async_posts(limit):
    async with aiohttp.ClientSession() as session:
        # timeframes: ["hour", "day", "month", "year"]. Leave parameter unspecified to get from all timeframes.
        # sorting: ["controversial", "new", "top", "best", "hot", "rising"]. Leave parameter unspecified to get from all sort criteria.
        posts = await community.posts(limit=limit, session=session)
        print(posts)


# Get posts that contain the specified keyword
async def async_search(keyword, limit):
    async with aiohttp.ClientSession() as session:
        found_posts = await community.search(keyword=keyword, limit=limit, session=session)
        print(found_posts)


# Get a community's wiki pages
async def async_wiki_pages():
    async with aiohttp.ClientSession() as session:
        wiki_pages = await community.wiki_pages(session=session)
        print(wiki_pages)


# Get a community's specified wiki page
async def async_wiki_page(page):
    async with aiohttp.ClientSession() as session:
        wiki_page = await community.wiki_page(page=page, session=session)
        print(wiki_page)

# asyncio.run(async_profile())
# asyncio.run(async_posts(limit=200))
# asyncio.run(async_search(keyword="artificial intelligence", limit=100))
# asyncio.run(async_wiki_pages())
# asyncio.run(async_wiki_page(page="config/description"))
````

### Communities (Subreddits) Data

````python
import asyncio
import aiohttp
from knewkarma import RedditCommunities

# Initialize RedditSub with the specified community
communities = RedditCommunities()


# Get all communities
async def async_all(limit):
    async with aiohttp.ClientSession() as session:
        all_communities = await communities.all(limit=limit, session=session)
        print(all_communities)


# Get default communities
async def async_default(limit):
    async with aiohttp.ClientSession() as session:
        default_communities = await communities.default(limit=limit, session=session)
        print(default_communities)


# Get new communities
async def async_new(limit):
    async with aiohttp.ClientSession() as session:
        new_communities = await communities.new(limit=limit, session=session)
        print(new_communities)


# Get popular communities
async def async_popular(limit):
    async with aiohttp.ClientSession() as session:
        popular_communities = await communities.default(limit=limit, session=session)
        print(popular_communities)

# asyncio.run(async_all(limit=500))
# asyncio.run(async_default(limit=200))
# asyncio.run(async_new(limit=100))
# asyncio.run(async_popular(limit=150))
````

### Posts Data

```python
import asyncio
import aiohttp
from knewkarma import RedditPosts

# Initialize RedditPosts
posts = RedditPosts()


# Get new posts
async def async_new(limit):
    async with aiohttp.ClientSession() as session:
        new_posts = await posts.new(limit=limit, session=session)
        print(new_posts)


# Get posts from the front-page
async def async_front_page(limit, sort, timeframe):
    async with aiohttp.ClientSession() as session:
        front_page_posts = await posts.front_page(limit=limit, sort=sort, timeframe=timeframe, session=session)
        print(front_page_posts)


# Get posts from a specified listing
async def async_listing(listing, limit, timeframe):
    async with aiohttp.ClientSession() as session:
        listing_posts = await posts.listing(listings_name=listing, limit=limit, timeframe=timeframe,
                                            session=session)
        print(listing_posts)

# timeframes: ["hour", "day", "month", "year"]. Leave parameter unspecified to get from all timeframes.
# sorting: ["controversial", "new", "top", "best", "hot", "rising"]. Leave parameter unspecified to get from all sort criteria.
# asyncio.run(async_new(limit=100))
# asyncio.run(async_front_page(limit=150, sort="top", timeframe="hour"))
# asyncio.run(async_listing(listing="best", limit=200, timeframe="month"))
```

### Search & Discovery

```python
import asyncio
import aiohttp
from knewkarma import RedditSearch

search = RedditSearch()


# Search users
async def async_search_users(query, limit):
    async with aiohttp.ClientSession() as session:
        users = await search.users(query=query, limit=limit, session=session)
        print(users)


# Search communities (subreddits)
async def async_search_communities(query, limit):
    async with aiohttp.ClientSession() as session:
        communities = await search.communities(query=query, limit=limit, session=session)
        print(communities)


# Search posts
async def async_search_posts(query, limit):
    async with aiohttp.ClientSession() as session:
        # timeframes: ["hour", "day", "month", "year"]. Leave parameter unspecified to get from all timeframes.
        # sorting: ["controversial", "new", "top", "best", "hot", "rising"]. Leave parameter unspecified to get from all sort criteria.
        posts = await search.posts(query=query, limit=limit, session=session)
        print(posts)

# asyncio.run(async_search_users(query="john", limit=150))
# asyncio.run(async_search_communities(query="ask", limit=200))
# asyncio.run(async_search_posts(query="cooking", limit=250))
```




