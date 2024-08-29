+++
title = "Reading and Writing with the BGG API in Go"
date = 2024-08-08T11:30:00Z
draft = false
tags = [ "Tutorial", "BGG", "Go" ]
categories = [ "Coding" ]
+++

It would be fair to say the BGG API ([BoardGameGeek](https://boardgamegeek.com/) for the uninitiated), is neither the most elegant nor intuitive API out there. It presents a curious blend of outdated XML, sparse documentation, and frustrating rate limits. Yet, despite these shortcomings, it holds a treasure trove of data on nearly every tabletop game imaginable.

However, there's a significant limitation: the API is ostensibly read-only, or at least, that's what the documentation would have you believe. Yet, applications like [Board Game Stats](https://www.bgstatsapp.com/) somehow manage to record plays and sync them with BGG. So, how is this possible, given the apparent lack of public write access?

In this short tutorial, I'll guide you through how you can not only read but also write to the BGG API. Even if you're not familiar with Go, this tutorial will offer insights into the general approach for gaining write access, which can be adapted to other programming languages.

## Initialising Go

Before diving into the code, you'll need to initialize your Go project. This is a straightforward process:

```
mkdir bgg-example
cd bgg-example
go mod init bgg-example
```

With this, you’ve set up a basic Go environment in which we can begin crafting our solution.

## Setup GoBGG

The next step involves setting up the GoBGG library, a small library that simplifies interactions with the BGG API.

## Login

The first action we need to perform is logging in to the API. To achieve this, we'll make a `POST` request to the `login/api/v1` endpoint, which returns cookies that we can then use to proxy requests back to BGG as an authenticated user. For simplicity, GoGeek provides a login method to handle this process.

```

```

It's worth noting that the cookies we’re after are HTTP-only, which means they aren't accessible from the browser. Instead, we must obtain these on the server side. Fortunately, the BGG API doesn’t discriminate against the origin of the client making the request, which allows us to craft our own login request, just as if the user were logging into BGG directly. Among the several cookie values returned, two key values are crucial for making subsequent requests to BGG: `bggusername` and `bggpassword`.

## Making a Request

Once authenticated, the next step is to perform actions by making requests to the BGG API. The key is to recreate the requests that BGG itself makes. Some requests are simpler to mimic than others. For example, by inspecting the network activity on the collection page of a user, we notice requests are made to `/geekcollection.php`, which contains form data. We can mimic these requests and create our own.

To streamline this process, GoGeek provides a number of actions. Let's explore how to add a game to our collection. The method below creates the request, and as you can see, it populates the form data. The key value we are modifying is the `objectid`, which corresponds to the unique BGG ID found in the URL of any game on the site.

```
func (c *Client) AddItem(id string) {
	form := url.Values{}
	form.Add("objecttype", "thing")
	form.Add("objectid", id)
	form.Add("addowned", "true")
	form.Add("addwish", "false")
	form.Add("wishlistpriority", "1")
	form.Add("force", "true")
	form.Add("ajax", "1")
	form.Add("action", "additem")
	c.doRequest(form)
}
```

The `AddItem` method generates the form data with the specified BGG ID and then makes a request using the following method:

```
func (c *Client) doRequest(values url.Values) {
	req, err := http.NewRequest(http.MethodPost, "https://boardgamegeek.com/geekcollection.php", strings.NewReader(values.Encode()))
	if err != nil {
		log.Fatal(err)
	}

	req.Header.Add("Content-Type", "application/x-www-form-urlencoded; charset=UTF-8")
	req.Header.Add("Cookie", fmt.Sprintf("bggusername=%s; bggpassword=%s", c.username, c.password))

	client := &http.Client{}
	resp, err := client.Do(req)
	if err != nil {
		log.Fatal(err)
	}

	defer resp.Body.Close()
	body, err := io.ReadAll(resp.Body)
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(string(body))
}
```

As illustrated, the doRequest method uses the cookie values obtained during login to authenticate the request. If the request is successful, a new game should be added to your collection, as below...

## Conclusion

As you can see with some clever tricks, the BGG API becomes much more flexible, enabling not just reading but also writing data. This opens up new possibilities for all sorts of custom integrations and hopefully encourages you to explore the full range of GoGeek's features.
