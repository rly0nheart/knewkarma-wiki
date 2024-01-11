# Usage

## CLI Usage (Including the Docker Container)

After installation, the *cli* instance can be called with the `knewkarma` command (or `docker run [container-name]` for
Docker Containers)

```text
knewkarma --help
```

```text
docker run -it my-knewkarma-container --help
```
```text
Usage: knewkarma [-h] [-t {hour,day,week,month,year}]
                 [-s {controversial,new,top,best,hot,rising}] [-l NUMBER]
                 [-j FILENAME] [-c FILENAME] [-u] [-v]
                 {community,communities,posts,search,user} ...

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                             Knew Karma CLI                                 ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

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

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃            Copyright © 2024 Richard Mwewa. All rights reserved.            ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

 MIT License

 Permission is hereby granted, free of charge, to any person obtaining a copy
 of Knew Karma and associated documentation files (the "Software"), to deal
 in the Software without restriction, including without limitation the rights
 to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
 copies of the Software, and to permit persons to whom the Software is
 furnished to do so, subject to the following conditions:

 The above copyright notice and this permission notice shall be included in a
 copies or substantial portions of the Software.

 THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
 AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM
 OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN TH
 SOFTWARE.
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

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                           Community (Subreddit)                            ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

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

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                  Examples                                  ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

                            Get community profile

 knewkarma community MachineLearning --profile

                             Get community posts

 knewkarma community MachineLearning --posts

        Search a community for posts that contain a specified keyword

 knewkarma community MachineLearning --search "artificial intelligence"

                          Get community's wiki pages

 knewkarma community MachineLearning --wiki-pages

                   Get community's specified wiki page data

 knewkarma community MachineLearning --wiki-page config/description
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

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                          Communities (Subreddits)                          ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

Options:
  -h, --help     show this help message and exit
  -a, --all      get all communities
  -d, --default  get default communities
  -n, --new      get new communities
  -p, --popular  get popular communities

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                  Examples                                  ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

                             Get all communities

 knewkarma communities --all

                           Get default communities

 knewkarma communities --default

                             Get new communities

 knewkarma communities --new

                           Get popular communities

 knewkarma communities --popular
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

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                   Posts                                    ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

Options:
  -h, --help            show this help message and exit
  -n, --new             get new posts
  -f, --front-page      get posts from the reddit front-page
  -l, --listing {best,controversial,popular,rising}
                        get posts from a specified listing

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                  Examples                                  ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

                                Get new posts

 knewkarma posts --new

                       Get posts from Reddit Front-Page

 knewkarma posts --front-page

                       Get posts from specified listing

 knewkarma posts --listing best
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

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                   Search                                   ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

Positional Arguments:
  query              search query

Options:
  -h, --help         show this help message and exit
  -u, --users        search users
  -p, --posts        search posts
  -c, --communities  search communities

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                  Examples                                  ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

                                 Search users

 knewkarma search john --users

                              Search communities

 knewkarma search ask --communities

                                 Search posts

 knewkarma search covid-19 --posts
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

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                    User                                    ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

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

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                                  Examples                                  ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

                               Get user profile

 knewkarma user  AutoModerator --profile

                              Get user comments

 knewkarma user  AutoModerator --comments

                              Get user comments

 knewkarma user  AutoModerator --posts

                   Get user's most recent comment activity

 knewkarma user AutoModerator --overview

            Get a user's posts that contain the specified keyword

 knewkarma user AutoModerator --search-posts rules

           Get a user's comment that contain the specified keyword

 knewkarma user AutoModerator --search-comments banned

                      Get communities moderated by user

 knewkarma user TheRealKSi --moderated-communities

     Get user's top n communities based on community frequency in n posts

 knewkarma --limit 500 user TheRealKSi --top-communities 10
```



