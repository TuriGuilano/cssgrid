# css grid notes

> implicit vs explicit

All the rows that we specify styles for are explicit rows.
All the other rows will be formatted based on the specified column grid with default hight styles. 
```
.container {
    display: grid;
    grid-gap: 20px;
    grid-template-columns: 200px 400px;
    grid-template-rows: 50px 100px 75px;
    /* sets hights for implicit defined rows to a height of 350px */
    grid-auto-rows: 350px;
}
```

> grid auto flow

When grid-auto-flow is being set to column the rows without specified styles are being added in the same row instead of on a new row.

You can then set the grid-auto-columns equal to a amount of px which will be adapted as the 'width' for the implicit created columns.

```
.container {
    display: grid;
    grid-gap: 20px;
    grid-template-columns: 400px 200px;
    grid-auto-flow: column;
    grid-auto-columns: 50px;
}
```

> Sizing tracks

Fractional units represent the amount of space left after all the elements laid out. So if we would have two columns defined with 15 items to be placed into these two columns and specify the thirth param inside grid-template-columns as 1fr; every thirth block in a row would have the width of the remaining space; the 1fr. ~in proportion to how many space is left~

```
.container {
    display: grid;
    grid-gap: 20px;
    border: 10px solid var(--yellow);
    grid-template-columns: 100px 100px 1fr;
}
```

If we specify ```grid-template-auto: auto;```
Our grid will set the width of each block equal to the block which has the biggest width based on its content. So it will automatically fit all the content in based on the block with the widest* content.

> css grid repeat

Grid repeat is pretty straight forward; it repeats the specified values:

```
.container {
    display: grid;
    grid-gap: 20px;
    grid-template-columns: repeat(2, 1fr 2fr); // will do the same as grid-template-comlumns: 1fr 2fr 1fr 2fr
}
```

> Sizing items

We can use the span value to size an individual item.

```
.container {
    display: grid;
    grid-gap: 20px;
    grid-template-columns: repeat(5, 1fr);
}

.item9 {
    background: goldenrod;
    grid-column: span 2;
    grid-row: span 2;
}
```

Item 9 will now take the width and height of the item next to it and the item below it.

> Placing grid items

We can place items specific by using grid-column-start and grid-column-end the same goes for rows.

We do need to specify the grid-template for both instances doh.
```
.container {
    display: grid;
    grid-gap: 20px;
    grid-template-columns: repeat(5, 1fr);
    grid-template-rows: repeat(5, 1fr);
}
.fish {
    grid-column-start: 2;
    grid-column-end: 5;
    /* this is the shorthand */
    grid-column: 2 / 5;
    /* we can do the same with spans, start at 1 and span two */
    grid-column: 1 / span 2;
    /* if you dont know how many columns you will end up with you can use */
    grid-column: 1 / -1; /* this will set a width 100% */
    grid-column: 1 / -2; /* this will set a width of 100% minus the last column% */
    /* we can do the same for rows but we do have to define the grid-template-row first */
    /* these styles will be based on the explicit defined grid. */
    grid-row: 1 / -1;
    background: #BADA55;
}
```

> Auto fit auto fill

The main thing here is we can specify 
``` 
    .container {
      display: grid;
      grid-gap: 20px;
      border: 10px solid var(--yellow);
      grid-template-columns: repeat(auto-fit, 150px);
    }
```

Our grid will then auto-fit these blocks into columns with a 150px width.
auto-fill does the exact same thing, the difference however; when using auto-fit if there are only 4 elements of 150px and you want to place the last block at the end of the grid, it will place it after the last block, because the column ends there. With auto-fill it goes to the actual end of that column and places it there. Sort of the same as a justify-content: flex-end on a item.

