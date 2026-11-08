---
layout: default
---

<section id="about">
  <p class="home-tagline">{{ site.description }}</p>
  <p>Hi! I'm Jonathan Mecham. At a time long past a small group of friends used to call me Meek. This is my Flyer, where I share what I'm working on and what I'm thinking about.</p>
</section>

## Projects

<ul class="link-list">
{%- for project in site.data.projects %}
  <li>
    <a href="{{ project.url }}"><strong>{{ project.name }}</strong></a>
    <span class="link-list-detail">{{ project.description }}</span>
  </li>
{%- endfor %}
</ul>

## Posts

<ul class="link-list">
{%- for post in site.posts %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
    <span class="link-list-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
  </li>
{%- endfor %}
</ul>

<section id="contact" class="contact">
  <h2>Contact</h2>
  <form id="contact-form" class="contact-form" action="https://formspree.io/f/xqppowlr" method="POST">
    <label for="contact-name">Name</label>
    <input id="contact-name" type="text" name="name" autocomplete="name" required>

    <label for="contact-email">Email</label>
    <input id="contact-email" type="email" name="email" autocomplete="email" required>

    <label for="contact-message">Message</label>
    <textarea id="contact-message" name="message" rows="6" required></textarea>

    <input type="hidden" name="_subject" value="New message from meekflyer.net">
    <!-- Honeypot: hidden from people, catches spam bots -->
    <input type="text" name="_gotcha" class="contact-hp" tabindex="-1" autocomplete="off" aria-hidden="true">

    <button type="submit">Send</button>
    <p id="contact-status" class="contact-status" role="status" aria-live="polite"></p>
  </form>
</section>

<script>
  (function () {
    var form = document.getElementById("contact-form");
    var status = document.getElementById("contact-status");
    form.addEventListener("submit", function (e) {
      e.preventDefault();
      var button = form.querySelector("button");
      button.disabled = true;
      status.textContent = "Sending…";
      fetch(form.action, {
        method: "POST",
        body: new FormData(form),
        headers: { Accept: "application/json" }
      }).then(function (res) {
        if (res.ok) {
          form.reset();
          status.textContent = "Thanks! Your message is on its way.";
        } else {
          return res.json().then(function (data) {
            status.textContent = (data.errors && data.errors.map(function (x) { return x.message; }).join(", ")) ||
              "Something went wrong. Please try again.";
          });
        }
      }).catch(function () {
        status.textContent = "Couldn't send. Check your connection and try again.";
      }).finally(function () {
        button.disabled = false;
      });
    });
  })();
</script>
