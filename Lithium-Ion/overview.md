---
title: Lithium Ion
---

<table>
  {% for row in site.data.lithium-ion %}
    {% if forloop.first %}
    <tr>
      {% for pair in row %}
        <th>{{ pair[0] }}</th>
      {% endfor %}
    </tr>
    {% endif %}

    <tr>
      {% for pair in row %}
        {% if pair[0] == 'picture' %}
          <td><img src="{{ pair[1] }}" alt="Image"></td>
        {% elsif pair[0] == 'result' %}
          {% if pair[1] == 'legit' %}
            <td style="background-color: green;">{{ pair[1] }}</td>
          {% elsif pair[1] == 'fraud' %}
            <td style="background-color: red;">{{ pair[1] }}</td>
          {% else %}
            <td>{{ pair[1] }}</td>
          {% endif %}
        {% elsif pair[0] == 'source' %}
          {% if pair[1] contains 'http://' or pair[1] contains 'https://' %}
            <td><a href="{{ pair[1] }}">{{ pair[1] }}</a></td>
          {% else %}
            <td>{{ pair[1] }}</td>
          {% endif %}
        {% else %}
          <td>{{ pair[1] }}</td>
        {% endif %}
      {% endfor %}
    </tr>
  {% endfor %}
</table>
