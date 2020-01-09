# Introduction

## Why another PHP Template Engine?

There are a lot of PHP Template Engine: Blade, Twig, Latte and much more. PHP itself is a templating language.
Among them, Twig is clearly the most robust one. Feature-rich, clean syntax and strong-enfoce secure checking.
However, each have its pros and cons. Most of the time, one of the cons is not frontend friendly.

Talking about Vue, the question immediately rise: Isn't Blade already have good support for Vue?

For starter, Blade is tightly bind to Laravel. Of course you can use it without Laravel core too, with several community solutions, for example: BladeOne

Technically you can use Vue in just any template engine, but it will likely resulted in a mess of template's own syntax and Vue's directives, something like:

```twig
{% for item in items %}
  <div class="title">
    {{ item.title }}
  </div>
  <div class="content">
    {{ item.body }}
  </div>
{% endfor %}

{% verbatim %}
  <ul>
    <li v-for="item in seq">
      {{ item.body }}
    </li>
  </ul>
{% endverbatim %}
```

Secondly, you just don't have a way to make use of Vue's Single File Component, which is, to me - a truly elegant way of templating.

___

Also, different than other template engine that also have their own template language (.twig for Twig, .blade.html for Blade), Velvet use [Vue's SFC] as its template language. Velvet itself is a template engine and only that.

## Why not just decouple?
Define the APIs, then use your PHP CMS/Framework as microservice (or `Headless CMS` as some may call it) is a common approach nowadays.
That's a good idea, but not always fit for real-world use. In many circumlates, you do not have enough resources to do that.

By resouces, many different aspects need to consider

**Time**

To run seperate servers for backend & frontend require resonable amount of time to plan to structure.
And if not do that right, this will lead to the following problem.

**Complexity**

For small to middle projects, the time for design the structure usually short, especically designing APIs, and make the backend & frontend communication ineffective.

**Performance**

For decoupled app, usually you make request to frontend server to get the SPA app.
The advantage comes it you do it right. Now the app now at client can make direct calls to backend server.
Backend server can use its own caching logic, while client also have its caching technique. Frontend can also use its own caching method. Now we have multi-level caching which can make great UX. Of course, the development process now much more complex.




### **JSON + client-side rendering** vs. **Server-side rendering + client hydration**

Personaly I like Json. Mostly for the ease of creating and using http-based API (REST, GraphQL and so on). But not all the time you want to have JSON respose. If your backend have only one consumer (frontend), design APIs may become unecessary overwork. Monolithic websites, as people call it, is still make up most of website in the world.