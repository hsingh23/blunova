Mavo Editability Guide

To make static HTML content editable and dynamic, use the property, mv-list, and mv-list-item attributes. Mavo
automatically binds these to your JSON data source.

1. Single Editable Items (`property`)
   Add the property attribute to any HTML tag to make its content editable.

- HTML:

1 <!-- Text becomes editable -->
2 <h1 property="heroTitle">Welcome Home</h1>
3
4 <!-- Image 'src' becomes editable -->
5 <img property="heroImage" src="images/default.jpg" alt="Hero" />

- JSON Output:

1 {
2 "heroTitle": "Welcome Home",
3 "heroImage": "images/default.jpg"
4 }

2. Editable Lists (`mv-list` & `mv-list-item`)
   Use mv-list on a container to create a collection of items. Use mv-list-item on the repeated element. Inside the item, use
   property for specific fields.

- HTML:

1 <div class="features-grid" mv-list>
2 <!-- This entire div repeats for each item in the list -->
3 <div class="feature-card" mv-list-item property="features">
4 <h3 property="title">Modern Design</h3>
5 <p property="description">Open concept living spaces.</p>
6 </div>
7 </div>

- JSON Output:


    1     {
    2       "features": [
    3         {
    4           "title": "Modern Design",
    5           "description": "Open concept living spaces."
    6         },
    7         {
    8           "title": "Prime Location",
    9           "description": "Heart of the city."

10 }
11 ]
12 }

Key Principles for LLMs:

1.  Unique Keys: Every root property attribute becomes a key in the root of the JSON object.
2.  Lists: mv-list creates an array in the JSON. The property attribute on the mv-list-item defines the array's name (e.g.,
    "features": []).
3.  Nested Data: Properties inside an mv-list-item become keys for objects inside that array.
4.  Auto-Saving: No extra JS is needed; Mavo handles the read/write operations to the file specified in mv-storage.
