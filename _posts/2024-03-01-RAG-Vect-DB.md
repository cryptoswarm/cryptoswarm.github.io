---
layout: distill
title: Exploring Vectors, Embeddings, and Vector Databases
description: Chat with your data essential notions.
date: 2024-03-01
show: true
giscus_comments: true

authors:
  - name: Mokhtar Safir
    url: "https://mokhtarsafir.dev/me/"
    # affiliations:
    #   name: IAS, Princeton

bibliography: 2024-03-16-rag.bib

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: TL;DR
  - name: Vectors
    subsections:
      - name: In mathematics and physics
      - name: In machine learning
      - name: Vector space
  - name: Embeddings
  - name: Vector Databases
  - name: Retrieval Augmented Generation
  - name: Indexes

# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
_styles: >
  .fake-img {
    background: #bbb;
    border: 1px solid rgba(0, 0, 0, 0.1);
    box-shadow: 0 0px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 12px;
  }
  .fake-img p {
    font-family: monospace;
    color: white;
    text-align: left;
    margin: 12px 0;
    text-align: center;
    font-size: 16px;
  }
---

<!-- **NOTE:**
Citations, footnotes, and code blocks do not display correctly in the dark mode since distill does not support the dark mode by default.
If you are interested in correctly adding dark mode support for distill, please open [a discussion](https://github.com/alshedivat/al-folio/discussions) and let us know. -->

## TL;DR

Explore the world of vectors, embeddings, and vector databases in mathematics, physics, and machine learning. Learn how to generate embeddings using Hugging Face Inference API and store them in vector databases for efficient retrieval. Discover the significance of vector databases in handling high-dimensional numerical vectors and their applications in various fields. Gain insights into retrieval-augmented generation (RAG) and indexing methods employed in vector databases.

## Vectors

### In mathematics and physics

According to Wikipedia Vector is: _a term that refers colloquially to some quantities that cannot be expressed by a single number (a scalar), or to elements of some vector spaces._<d-cite key="vectorinmath"></d-cite>. Here you can <a href="https://www.mathsisfun.com/algebra/vectors.html">play with vectors</a>

### In machine learning

According to Algolia's documentation, vectors signify : _input data, including bias and weight. In the same way, output from a machine-learning model (for example, a predicted class), can be put into vector format._<d-cite key="vectorinmachinglearningalgolia"></d-cite>

### Vector space

## Embeddings

Embeddings are numerical representations of documents, which can include various types such as text, images, videos, and audio. These embeddings capture semantic relationships and contextual information, enabling algorithms to perform tasks such as similarity analysis, recommendation systems, and natural language understanding.

Let's embed(encode) the above paragraph using Hugging Face Inference API. If you want to follow along you need to create an account at <a href="https://huggingface.co/join">Hugging Face</a> . Also, an access token with write permission is required.

Using a tool such as Postman, you can generate the embedding by sending a POST request to the endpoint {% highlight javascript %} https://api-inference.huggingface.co/pipeline/feature-extraction/{model_id}{% endhighlight %} where model_id corresponds to {% highlight javascript %}sentence-transformers/all-MiniLM-L6-v2{% endhighlight %}

{% highlight javascript %}
{
"inputs": "Embeddings are numerical representations of documents, ...",
"options":{
"wait_for_model": true
}
}
{% endhighlight %}

The generated embedding is a list of 384 numbers (dimensions of the data), representing the semantic meaning of the text.

{% highlight javascript %}
{
[
-0.003196842037141323,
-0.07144313305616379,
0.06496944278478622,
...
]
}
{% endhighlight %}

The length of this list varies depending on the model employed. If `OpenAI text-embedding-ada-002 model` is utilized, the length of this list would be 1536 dimensions.

Depending on the index schema, additional fields, including the text and the equivalent embedding, must be stored in an index of a vector database for future retrieval. But what exactly is a vector database?

## Vector Databases

Vector databases specialize in handling vector data, which are mathematical entities represented across multiple dimensions. They find extensive application in semantic searches, retrieval augmentation generation (RAG), and geographic information systems (GIS). Essentially, they enable the storage and retrieval of more relevant results in a highly scalable manner.

One of the most common ways to store and search over unstructured data is through vector databases.

At the core of a vector database is its ability to determine content that is close in meaning to a given query. This is achieved by first embedding the data and storing the resulting embedding vectors. During query time, an embedding is generated for the query, which is then used to query the stored data and retrieve the entries that are most similar to the embedded query.

In contrast to traditional databases, which store data in rows and columns, vector databases store data in the form of vectors. This difference in storage allows for more efficient handling of high-dimensional numerical vectors, which is essential for tasks such as similarity search and content recommendation.

---

## Retrieval Augmented Generation

In the context of generative AI, retrieval-augmented generation (RAG) is a method that uses a combination of retrieving existing information from a large dataset and creatively generating new content from that retrieved information. This mimics the way humans often come up with new ideas: by building upon and remixing what we've learned before.

---

## Indexes

The vector database indexes vectors using an algorithm such as PQ, LSH, or HNSW (more on these below). This step maps the vectors to a data structure that will enable faster searching.

Just wrap the text you would like to show up in a footnote in a `<d-footnote>` tag.
The number of the footnote will be automatically generated.<d-footnote>This will become a hoverable footnote.</d-footnote>

---

## Layouts

The main text column is referred to as the body.
It is the assumed layout of any direct descendants of the `d-article` element.

<div class="fake-img l-body">
  <p>.l-body</p>
</div>

For images you want to display a little larger, try `.l-page`:

<div class="fake-img l-page">
  <p></p>
</div>

All of these have an outset variant if you want to poke out from the body text a little bit.
For instance:

<div class="fake-img l-body-outset">
  <p>.l-body-outset</p>
</div>

<div class="fake-img l-page-outset">
  <p>.l-page-outset</p>
</div>

Occasionally you’ll want to use the full browser width.
For this, use `.l-screen`.
You can also inset the element a little from the edge of the browser by using the inset variant.

<div class="fake-img l-screen">
  <p>.l-screen</p>
</div>
<div class="fake-img l-screen-inset">
  <p>.l-screen-inset</p>
</div>

The final layout is for marginalia, asides, and footnotes.
It does not interrupt the normal flow of `.l-body` sized text except on mobile screen sizes.

<div class="fake-img l-gutter">
  <p>.l-gutter</p>
</div>

---

## Other Typography?

Emphasis, aka italics, with _asterisks_ (`*asterisks*`) or _underscores_ (`_underscores_`).

Strong emphasis, aka bold, with **asterisks** or **underscores**.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~

1. First ordered list item
2. Another item
   ⋅⋅\* Unordered sub-list.
3. Actual numbers don't matter, just that it's a number
   ⋅⋅1. Ordered sub-list
4. And another item.

⋅⋅⋅You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

⋅⋅⋅To have a line break without a paragraph, you will need to use two trailing spaces.⋅⋅
⋅⋅⋅Note that this line is separate, but within the same paragraph.⋅⋅
⋅⋅⋅(This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)

- Unordered list can use asterisks

* Or minuses

- Or pluses

[I'm an inline-style link](https://www.google.com)

[I'm an inline-style link with title](https://www.google.com "Google's Homepage")

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../blob/master/LICENSE)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

URLs and URLs in angle brackets will automatically get turned into links.
http://www.example.com or <http://www.example.com> and sometimes
example.com (but not on Github, for example).

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com

Here's our logo (hover to see the title text):

Inline-style:
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

Reference-style:
![alt text][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"

Inline `code` has `back-ticks around` it.

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

```python
s = "Python syntax highlighting"
print s
```

```
No language indicated, so no syntax highlighting.
But let's throw in a <b>tag</b>.
```

Colons can be used to align columns.

| Tables        |      Are      |  Cool |
| ------------- | :-----------: | ----: |
| col 3 is      | right-aligned | $1600 |
| col 2 is      |   centered    |   $12 |
| zebra stripes |   are neat    |    $1 |

There must be at least 3 dashes separating each header cell.
The outer pipes (|) are optional, and you don't need to make the
raw Markdown line up prettily. You can also use inline Markdown.

| Markdown | Less      | Pretty     |
| -------- | --------- | ---------- |
| _Still_  | `renders` | **nicely** |
| 1        | 2         | 3          |

> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can _put_ **Markdown** into a blockquote.

Here's a line for us to start with.

This line is separated from the one above by two newlines, so it will be a _separate paragraph_.

This line is also a separate paragraph, but...
This line is only separated by a single newline, so it's a separate line in the _same paragraph_.
