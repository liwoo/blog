---
title: "Making the Web an Inclusive Place: How to Design for Accessibility"
author: "Jeremiah Chienda <jeremiah@chienda.com>"
date: "2019-08-07"
duration: "8 min read"
topic: "Web Development"
tags: ["Digital Health", "Malawi", "OpenHIE", "Healthcare Technology"]
---

# Making the Web an Inclusive Place: How to Design for Accessibility

From its inception, the web was designed for humans, not machines. It was crafted with the idea that everyone, including those with visual impairments, should be able to access and consume information freely. This ethos was evident in the rich and descriptive markup that the HTML specification provided.

Yet, as the web evolved and JavaScript frameworks began to dominate, we saw a shift. There was a move away from native web markup towards the world of "Components". The result? Web developers started abstracting their sites to the point where the underlying HTML became just a messy stew of div tags. And let me tell you, maestro, that's a tragedy for accessibility.

To counteract this trend and ensure that our web remains inclusive, I've outlined some simple heuristics I employ when crafting web applications.

## 1. **Nav for Building Navbars**

When you're designing navigation bars, use the `<nav>` element. It's a semantic way to indicate that a section of your site contains navigation links.

**Example:**

```html
<nav>
  <ul>
    <li><a href="#home">Home</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
```
