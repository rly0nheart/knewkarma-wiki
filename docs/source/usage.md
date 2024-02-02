# Usage
## CLI (and Docker Container) Usage

After installation, the *cli* instance can be called with the `knewkarma` command (or `docker run [container-name]` for
Docker Containers)


```commandline
knewkarma --help
```

```commandline
docker run -t my-knewkarma-container --help
```
#### Pip installation
```text
knewkarma --help
```
#### Docker container
```text
docker run -t knewkarma --help
```
```commandline
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

```commandline
knewkarma community --help
```

```commandline
docker run -it my-knewkarma-container community --help
=======
### Community (Subreddit) Operations Usage
#### Pip installation
```text
knewkarma community --help
```
#### Docker container
```commandline
docker run -it knewkarma community --help
```
```commandline
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
```commandline
knewkarma communities --help
```
```commandline
docker run -it my-knewkarma-container communities --help
=======
### Communities' (Subreddits) Operations Usage
#### Pip installation
```text
knewkarma communities --help
```
#### Docker container
```commandline
docker run -it knewkarma communities --help
```
```commandline
Usage: knewkarma communities [-h] [-a] [-d] [-n] [-p]


Options:
  -h, --help     show this help message and exit
  -a, --all      get all communities
  -d, --default  get default communities
  -n, --new      get new communities
  -p, --popular  get popular communities
```

### Post Operations' Usage
```commandline
knewkarma post --help
```
```commandline
Positional Arguments:
  id              post id
  community       post source community

Options:
  -h, --help      show this help message and exit
  -p, --profile   get post 'profile' data
  -c, --comments  get post comments

```
### Posts Operations' Usage

```commandline
knewkarma posts --help
```

```commandline
docker run -it my-knewkarma-container posts --help
=======
### Posts' Operations Usage
#### Pip installation
```text
knewkarma posts --help
```
#### Docker container
```commandline
docker run -it knewkarma posts --help
```
```commandline
Usage: knewkarma posts [-h] [-n] [-f] [-l {best,controversial,popular,rising}]


Options:
  -h, --help            show this help message and exit
  -n, --new             get new posts
  -f, --front-page      get posts from the reddit front-page
  -l, --listing {best,controversial,popular,rising}
                        get posts from a specified listing
```

### Search Operations' Usage

```commandline
knewkarma search --help
```

```commandline
docker run -it my-knewkarma-container search --help
=======
### Search Operations Usage
#### Pip installation
```text
knewkarma search --help
```
#### Docker container
```text
docker run -it knewkarma search --help
```
```commandline
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

```commandline
knewkarma user --help
```

```commandline
docker run -it my-knewkarma-container user --help
=======
### User Operations Usage
#### Pip installation
```text
knewkarma user --help
```
#### Docker container
```text
docker run -it knewkarma user --help
```
```commandline
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



