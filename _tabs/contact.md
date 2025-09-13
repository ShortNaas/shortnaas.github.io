---
layout: page
icon: fas fa-envelope
order: 4
---

<h1>Contact Me</h1>

<form action="https://formspree.io/f/yourformid" method="POST">
  <label for="name">Name:</label><br>
  <input type="text" id="name" name="name" required><br>

  <label for="email">Email:</label><br>
  <input type="email" id="email" name="_replyto" required><br>

  <label for="message">Message:</label><br>
  <textarea id="message" name="message" rows="6" required></textarea><br>

  <button type="submit">Send</button>
</form>
