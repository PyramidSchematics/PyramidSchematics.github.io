---
layout: post
title: "Sample Post"
author: Ed 
tags: [Sample]
categories: Sample
---

# Markup Syntax Highlighting

Syntax highlighting[^1] is a feature that displays source code.
This feature facilitates writing in a structured language such as a programming language or a markup language as it makes import things visually distinct.


### GFM Code Blocks

GitHub Flavored Markdown [fenced code blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/) are supported. To modify styling and highlight colors edit `/_sass/syntax.scss`.

```css
#container {
  float: left;
  margin: 0 -240px 0 0;
  width: 100%;
}
```

{% highlight scss linenos %}
.highlight {
  margin: 0;
  padding: 1em;
  font-family: $monospace;
  font-size: $type-size-7;
  line-height: 1.8;
}
{% endhighlight %}

```html
{% raw %}<nav class="pagination" role="navigation">
  {% if page.previous %}
    <a href="{{ site.url }}{{ page.previous.url }}" class="btn" title="{{ page.previous.title }}">Previous article</a>
  {% endif %}
  {% if page.next %}
    <a href="{{ site.url }}{{ page.next.url }}" class="btn" title="{{ page.next.title }}">Next article</a>
  {% endif %}
</nav><!-- /.pagination -->{% endraw %}
```

```ruby
module Jekyll
  class TagIndex < Page
    def initialize(site, base, dir, tag)
      @site = site
      @base = base
      @dir = dir
      @name = 'index.html'
      self.process(@name)
      self.read_yaml(File.join(base, '_layouts'), 'tag_index.html')
      self.data['tag'] = tag
      tag_title_prefix = site.config['tag_title_prefix'] || 'Tagged: '
      tag_title_suffix = site.config['tag_title_suffix'] || '&#8211;'
      self.data['title'] = "#{tag_title_prefix}#{tag}"
      self.data['description'] = "An archive of posts tagged #{tag}."
    end
  end
end
```

### Code Blocks in Lists

Indentation matters. Be sure the indent of the code block aligns with the first non-space character after the list item marker (e.g., `1.`). Usually this will mean indenting 3 spaces instead of 4.

1. Do step 1.
2. Now do this:

   ```ruby
   def print_hi(name)
     puts "Hi, #{name}"
   end
   print_hi('Tom')
   #=> prints 'Hi, Tom' to STDOUT.
   ```

3. Now you can do this.

### GitHub Gist Embed

An example of a Gist embed below:

<script defer src="https://gist.github.com/sylhare/dad7ed1ef3d13614c77c4ebadf8a11c3.js"></script>

Here is how it looks like:

{% highlight html %}
{% raw %}
   <script src="https://gist.github.com/sylhare/dad7ed1ef3d13614c77c4ebadf8a11c3.js">
   </script>
{% endraw %}
{% endhighlight %}

<br>

[^1]: {% include citation.html key="highlight" %}



# Markdown and HTML

Jekyll supports the use of [Markdown](http://daringfireball.net/projects/markdown/syntax) with inline HTML tags which makes it easier to quickly write posts with Jekyll, without having to worry too much about text formatting. A sample of the formatting follows.

## Table of content

<!-- To be placed at the beginning of the post, it is where the table of content will be generated -->
* TOC
  {:toc}
*
You need to put this at the beginning of the page where you want the table of content to be displayed

```html
* TOC
{:toc}
```

It will then render the markdown and html titles (lines that begins with `#` or using the `<h1></h1>` tages)


## Title

### Subtitle

Tables have also been extended from Markdown:

| First Header | Second Header |
|--------------|---------------|
| Content Cell | Content Cell  |
| Content Cell | Content Cell  |

Here's an example of an image, which is included using Markdown:

![Image of a glass on a book]({{ "/assets/img/pexels/book-glass.jpeg" | relative_url }})

This is another example of list:

 - list of things
   1. Sub list
   2. of Other things
   3. with numbers
 - And many more
   - Sub sub list
     - can go on ...
       - and on ...
         - and on !
   - That's it.

### Other subtitle

Highlighting for code in Jekyll is done using Base16 or Rouge. This theme makes use of Rouge by default.

{% highlight js %}
// count to ten
for (var i = 1; i <= 10; i++) {
    console.log(i);
}

// count to twenty
var j = 0;
while (j < 20) {
    j++;
    console.log(j);
}
{% endhighlight %}

### Math

Type on Strap uses KaTeX to display maths. Equations such as $$S_n = a \times \frac{1-r^n}{1-r}$$ can be displayed inline.

Alternatively, they can be shown on a new line:

$$ f(x) = \int \frac{2x^2+4x+6}{x-2} $$

And in your markdown file:

```markdown
$$ f(x) = \int \frac{2x^2+4x+6}{x-2} $$
```


### Expandable content

Click on the expandable content to display it:

<details>
    <summary>Click here!</summary>
    Now you see me
</details>

And in your markdown file:

```html
<details>
    <summary>Click here!</summary>
    Now you see me
</details>
```

# Mermaid

## Mermaid

Diagrams with mermaid, make sure it is enabled in the `_config.yml`.
Here is a simple example:

```html
<!-- To generate a diagram -->
<div class="mermaid">
sequenceDiagram
    Alice->>John: Hello John, how are you?
    John-->>Alice: Great!
</div>
```

> 💡 Now render also work with the GitHub markdown highlight.
{% highlight markdown %}
```mermaid
sequenceDiagram
    Alice->>John: Hello John, how are you?
    John-->>Alice: Great!
```
{% endhighlight %}
That will be rendered into this:

{% include aligner.html images="mermaid-example.png" column=auto %}

You can also go with more complex features and diagrams from the [documentation](https://mermaid-js.github.io/mermaid/),
and try it out with the [live editor](https://mermaid.live/).

### SequenceDiagram

<div class="mermaid">
sequenceDiagram
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop Healthcheck
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts prevail!
    John-->>Alice: Great!
    John->>Bob: How about you?
    Bob-->>John: Jolly good!
</div>

### Flow

```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%

flowchart TD
    A[Christmas] -->|Get money| B(Go shopping)
    B --> C{Let me think}
    C -->|One| D[Laptop]
    D ~~~ E
    C -->|Two| E[iPhone]
    C -->|Three| F[fa:fa-car Car]
    %% Grinch
```

### Class

```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%

classDiagram
    Animal <|-- Duck
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
      +String beakColor
      +swim()
      +quack()
    }
    class Fish{
      -int sizeInFeet
      -canEat()
    }
    class Zebra{
      +bool is_wild
      +run()
    }
```

### State

```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%

stateDiagram-v2
    [*] --> Still
    Still --> [*]
    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
```

### ER

```mermaid
erDiagram
    CUSTOMER }|..|{ DELIVERY-ADDRESS : has
    CUSTOMER ||--o{ ORDER : places
    CUSTOMER ||--o{ INVOICE : "liable for"
    DELIVERY-ADDRESS ||--o{ ORDER : receives
    INVOICE ||--|{ ORDER : covers
    ORDER ||--|{ ORDER-ITEM : includes
    PRODUCT-CATEGORY ||--|{ PRODUCT : contains
    PRODUCT ||--o{ ORDER-ITEM : "ordered in"
```

### Gantt

```mermaid
gantt
    title A Gantt Diagram
    dateFormat  YYYY-MM-DD
    section Section
    A task           :a1, 2014-01-01, 30d
    Another task     :after a1  , 20d
    section Another
    Task in sec      :2014-01-12  , 12d
    another task      : 24d
```

### User Journey

```mermaid
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 3: Me
```

### Git

```mermaid
gitGraph
    commit
    commit
    branch develop
    checkout develop
    commit
    commit
    checkout main
    merge develop
    commit
    commit
```

### Pie

```mermaid
pie title Pets adopted by volunteers
    "Dogs" : 386
    "Cats" : 85
    "Rats" : 15
```

### Mindmap

```mermaid
mindmap
  root((mindmap))
    Origins
      Long history
      ::icon(fa fa-book)
      Popularisation
        British popular psychology author Tony Buzan
    Research
      On effectivness<br/>and features
      On Automatic creation
        Uses
            Creative techniques
            Strategic planning
            Argument mapping
    Tools
      Pen and paper
      Mermaid
```

### QuadrantChart

```mermaid
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
```

### XYChart

```mermaid
    xychart-beta
    title "Sales Revenue"
    x-axis [jan, feb, mar, apr, may, jun, jul, aug, sep, oct, nov, dec]
    y-axis "Revenue (in $)" 4000 --> 11000
    bar [5000, 6000, 7500, 8200, 9500, 10500, 11000, 10200, 9200, 8500, 7000, 6000]
    line [5000, 6000, 7500, 8200, 9500, 10500, 11000, 10200, 9200, 8500, 7000, 6000]
```


# Feature Images


Hopefully you will find enough information about how to set images in your blog here.
This is an example of a post which includes a feature image specified in the front matter of the post.
The feature image spans the full-width of the page, and is shown with the title on permalink pages:

```yaml
feature-img: "assets/img/feature-img/desk-messy.jpeg"
thumbnail: "assets/img/thumbnails/feature-img/desk-messy.jpeg"
```

You can also use a thumbnail, a smaller version of the same image to improve loading of the page.
The thumbnail will also be used when you share your article on other platform (linkedin, whatsapp, facebook, ...).

>  - And now it is working

You can also add images aligned in your post using the `aligner` include.
Make sure to separate all of the image path from in a string separated with `,`.
It by default look into `assets/img/` so give the path from there, example:

{% highlight ruby %}
{% raw %}
{% include aligner.html images="pexels/book-glass.jpeg,triangle.png" caption="A caption under the images" %}
{% endraw %}
{% endhighlight %}

{% include aligner.html images="pexels/book-glass.jpeg,feature-img/desk-messy.jpeg" caption="A caption under the images" %}


Here you have two images side by side, but you can set more and set the amount per columns
(by specifying the number of columns or let it be automatic using `"auto"`):

{% highlight ruby %}
{% raw %}
{% include aligner.html images="portfolio/cabin.png,portfolio/cake.png,portfolio/circus.png" column=3 %}
{% endraw %}
{% endhighlight %}

{% include aligner.html images="portfolio/cabin.png,portfolio/cake.png,portfolio/circus.png" column=3 %}

it also works with only one images, it is made to display it smaller than normally.
However you can just use the Markdown way of doing it to get the image normal sized and centered.

{% highlight ruby %}
{% raw %}
# Markdown way
![Travel]({{ "/assets/img/pexels/computer.jpeg" | relative_url}})
# Aligner with only one image
{% include aligner.html images="pexels/computer.jpeg" %}
{% endraw %}
{% endhighlight %}

{% include aligner.html images="pexels/computer.jpeg" %}




> Suspendisse lectus leo, consectetur in tempor sit amet, placerat quis neque

Etiam luctus porttitor lorem, sed suscipit est rutrum non. Curabitur lobortis nisl a enim congue semper. Aenean commodo ultrices imperdiet. Vestibulum ut justo vel sapien venenatis tincidunt.

$$ \Theta \ne \Gamma $$




