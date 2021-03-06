Simplest case, no columns
-------------------------

### Basic table

![display:table](images/tut_basic.png)

```html
    <% request.setAttribute( "test", new TestList(10, false) ); %>

    <display:table name="test" />
```

The simplest possible usage of the table tag is to point the table tag
at a `java.util.List` implementation and do nothing else. The table tag
will iterate through the list and display a column for each property
contained in the objects.

Typically, the only time that you would want to use the tag in this
simple way would be during development as a sanity check. For
production, you should always define at least a single column.

### Basic, columns

![display:table with columns](images/tut_columns.png)

```html
    <% request.setAttribute( "test", new TestList(10, false) ); %>

    <display:table name="test">
      <display:column property="id" title="ID" />
      <display:column property="name" />
      <display:column property="email" />
      <display:column property="status" />
      <display:column property="description" title="Comments"/>
    </display:table>
```

This example starts to show you how to use the table tag. You point the
table tag at a datasource (a List), then define a number of columns with
properties that map to accessor methods (getXXX) for each object in the
List.

Note that you have one column tag for every column that you want to
appear in the table. And, the column specifies what property is shown in
that particular row.

You can define the content of a column by adding a property attribute to
the column tag or adding a content to the tag.

```html
       <display:column property="email" />
       <display:column title="email">email@it.com</display:column>
```

There are two ways to define the content of a column. Of course, in the
tag body you can use scriptlets or other custom tags. Using the property
attribute to define the content of a column is usually faster and works
better with sorting. If you add a property attribute the tag body is
ignored.

Adding content in the column body you can easily concatenate or
decorate fields available in objects in the list. See the [implicit
objects](tut_implicitobjects.html) chapter for more details.

The property attribute specifies what getXXX method is called on each
item in the list. So for the second column, getName is called. By
default the property name is used as the header of the column unless you
explicitly give the column a title.

