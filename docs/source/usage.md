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
                 [-e FILETYPES] [-u] [-v]
                 {community,communities,posts,search,user} ...



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
  -e, --export FILETYPES
                        a comma-separated list of file types to export the
                        output to (supported: csv,html,json,xml)
  -u, --updates         check for updates on run
  -v, --version         show program's version number and exit
```

You can further view individual operation mode usages by calling `knewkarma` with an operation mode name and
the `-h/--help` flag.

### Community (Subreddit) Operations' Usage

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

### Communities (Subreddits) Operations' Usage
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


### Posts Operations' Usage

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

### Search Operations' Usage

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

### User Operations' Usage

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



