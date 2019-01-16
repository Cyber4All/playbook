## Block Element Modifier (BEM)

### Placing Blocks in other Blocks

When a block is contained in another block, it should be named is if it is an element of its parent. 
Then, when naming elements inside of the child block, they will only use the block name of the direct parent.
Therefore, if we have a template arranged as follows:

```html
<a>
  ...
  <b>
    <c></c>
  </b>
</a>
```

Our pattern for naming our classes would be:

```html
<a class="block1">
  ...
  <b class="block1__block2">
    <c class="block2__element"></c>
  </b>
</a>
```

*More on BEM can be found on its official home page, http://getbem.com/*
