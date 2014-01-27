A great filter recently [made its way into](https://github.com/Shopify/liquid/pull/267) the Liquid templating system that makes it easy to output a default value if the variable you pass it turns out to be empty. Take this example of a metatag where I want to output the page title if it's populated, otherwise I want to output some default value instead:

{% highlight html %}
{% raw %}
<meta property="og:title" content="{{ page.title | default: 'Paul Herron, Web Developer' }}" >
{% endraw %}
{% endhighlight %}

It's a lot more elegant than putting that same logic inside if/else blocks within your view.

I was scratching my head trying to work out why this wasn't working in Jekyll, and it looks like this new feature [hasn't landed yet in the version of Liquid that Jekyll uses](https://github.com/jekyll/jekyll/issues/1666#issuecomment-27319857). That's easily remedied by including this plugin in your Jekyll site. It just takes [the new `default` method](https://github.com/djreimer/liquid/commit/5db1695694e1cbf12892d5dd67c7773282a669af) as-is from a recent Liquid version and makes it available to Jekyll.


Installation
------------

Copy `default_filter.rb` into the `_plugins` directory of your Jekyll site.
