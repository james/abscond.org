---
layout: post
title: "Family Board Game Christmas Presents via Amazon Prime"
date: "2021-12-19"
# subtitle: ""
# tags: ['note']
#categories: []
---

You should have organised your Christmas presents months ago. You should support local businesses. You should have hand wrapped all of the presents and posted them second class last week.

But you haven't, and the world is shutting down due to coronavirus again, and are you going to queue up at the post office on Wednesday? Give yourself a break.

Here are 30 board games that have been [reviewed well](https://www.youtube.com/watch?v=wzhUXlGIDFY) or recommended to me. At time of posting, they're all available on Amazon Prime next day delivery at the prices I have listed. I have included the number of players, so you can find the right game for each household size. I'll let you research from there.

This is what I did last year, and it worked well.

They're Amazon affiliate links. On the small chance I get any money out of it, I'll give it to the [IWGB Couriers and Logistics Union](https://iwgb.org.uk/en/page/clb/).

<table class="table">
  <thead class="thead-light">
    <tr>
      <th scope="col">Name</th>
      <th scope="col">№ of players</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    {% for board_game in site.data.board_games %}
      <tr>
        <td>
          <a href="{{ board_game.Link }}">{{ board_game.Name }}</a>
        </td>
        <td>{{ board_game.Players }}</td>
        <td>{{ board_game.Price }}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>

Hopefully that makes someone's week less stressful.