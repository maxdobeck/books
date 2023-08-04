# Books
Built using mdbook cli. 


## Using mdbook
`mdbook serve --open` will only watch the `src` directory. 

Or you can pass the directory like `mdbook serve --open ./sauce/locale-and-language` to open a book while you're not in that books root.

Installation and basics -> https://rust-lang.github.io/mdBook/guide/installation.html.


### Produce PDF
https://github.com/HollowMan6/mdbook-pdf

The wonderful mdbook-pdf package does the job. A pdf is produced in `/book/pdf`. Looks great!  
### Produce HTML
HTML output specified. See https://github.com/maxdobeck/books/blob/430db037396c19d96291cea3ec3b50afe9027b81/sauce/locale-and-language/book.toml#L8 for a slimmed down example. The output should live under `/book/html` and while its slightly redundant it is nice for copy-paste purposes to have it live there and in the root of `/book`.