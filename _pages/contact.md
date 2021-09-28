---
layout: page
permalink: /contact/
title: contact
nav: true
social: true
---

Feel free to reach out to me with the form below. Just leave your
information, and I will get back to you ASAP to the email you provided.

{% include email_form.html %}
{% if page.social %}

<div class="social">
    <div class="contact-icons">
        {% include social.html %}
    </div>
    <div class="contact-note">{{ site.contact_note }}</div>
</div>
{% endif %}
