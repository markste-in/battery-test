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
        {% assign cleaned_value = pair[1] | strip %}
        {% if pair[0] == 'picture' %}
          <td><img src="{{ cleaned_value }}" alt="Image" style="max-width: 200px; max-height: 150px;"></td>
        {% elsif pair[0] == 'result' %}
          {% if cleaned_value == 'legit' %}
            <td style="background-color: #90ee90;">{{ cleaned_value }}</td> <!-- Light green -->
          {% elsif cleaned_value == 'fraud' %}
            <td style="background-color: #ffcccb;">{{ cleaned_value }}</td> <!-- Light red -->
          {% else %}
            <td>{{ cleaned_value }}</td>
          {% endif %}
        {% elsif pair[0] == 'source' %}
          {% if cleaned_value contains 'http://' or cleaned_value contains 'https://' %}
            <td><a href="{{ cleaned_value }}">{{ cleaned_value }}</a></td>
          {% else %}
            <td>{{ cleaned_value }}</td>
          {% endif %}
        {% else %}
          <td>{{ cleaned_value }}</td>
        {% endif %}
      {% endfor %}
    </tr>
  {% endfor %}
</table>
