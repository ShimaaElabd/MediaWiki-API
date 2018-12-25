# MediaWiki API

The MediaWiki action API is a web service that allows access to some wiki-features like authentication, 
page operations, and search. It can provide Meta information about the wiki and the logged-in user.

![mediawiki_logo_without_tagline](https://user-images.githubusercontent.com/25883512/50425443-be1d3f00-087e-11e9-8607-5a736e11fc8d.png)

Check out the docs: https://www.mediawiki.org/wiki/API:Main_page#A_simple_example

## Wptools Library

There are a bunch of different access libraries for MediaWiki to satisfy the variety of programming languages that exist. 
Here is a list for Python. This is pretty standard for most APIs.
Some libraries are better than others, For a MediaWiki, the most up to date and human readable one in Python is called wptools. 

## Mashup: APIs and JSON

Downloading images may seem tricky from a reading and writing perspective,
in comparison to text files which can be read line by line, for example.
Image files aren't special—they're just binary files. To interact with them, We don't need special software 
(like Photoshop or something) that "understands" images.
We can use regular file opening, reading, and writing techniques, like this:

![image](https://user-images.githubusercontent.com/25883512/50425927-87005b00-0889-11e9-9894-b4ce86e18b56.png)

        
But this technique can be error-prone. It will work most of the time, but sometimes the file which be written to will be damaged.        
This type of error is why the requests library maintainers recommend using the PIL library (short for Pillow) and BytesIO from the
io library for non-text requests, like images. They recommend that you access the response body as bytes, 
for non-text requests. For example, to create an image from binary data returned by a request:

![image](https://user-images.githubusercontent.com/25883512/50425934-9e3f4880-0889-11e9-873d-ed656fa255e8.png)

This code above will at least warn us with an error message, at which point we can manually download the problematic images.

So, In this Notebook I gather the last piece of data for the Roger Ebert review word clouds now: the movie poster image files.
and keep each image's URL to add to the master DataFrame later.

Though I've used a loop to minimize repetition in order to query the MediaWiki API using wptools to get a movie poster URL via 
each page object's image attribute.
Using that URL, will programmatically download that image into a folder called bestofrt_posters.

