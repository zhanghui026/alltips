# Vim Tips

## Vim 安装

> brew install vim

## Vim懒人插件

* [10 tips]: https://medium.com/@huntie/10-essential-vim-plugins-for-2018-39957190b7a9


## Vim tips

[move tips](https://stackoverflow.com/questions/8750275/vim-super-fast-navigation)

```
Try $ vimtutor, it will teach you everything you need to know to get started.

hjkl are the tip of the top of the iceberg and very rarely used, at least in my case.

wWEe and BbgegE all allow to move word by word:

w and e go forward, W and E take whitespace and punctuation into account

" here the * marks the default location of the cursor
" and each letter shows where you jump when you hit the key.

Latin: Lorem ipsum dolor sit amet.
                   *   e   e    e
                   *   E   E     E
*    w w     w     w     w   w   w
*      W     W     W     W   W   W
b and ge go backward, B and gE take whitespace and punctuation into account

Latin: Lorem ipsum dolor sit amet.
b    b b     b     *
B      B     B     *
     ge    ge    ge*
    ge
     gE    gE    gE*
fFtT are used to reach for a particular character on the current line and ;, are used to repeat that motion, in the same direction for ;and in the opposite direction for ,:

fm jumps ON the next m forward, F goes backward

Latin: Lorem ipsum dolor sit amet.
*          fm    ;            ;
           ;     Fm          *
tm jumps BEFORE the next m forward, T goes backward

Latin: Lorem ipsum dolor sit amet.
*         tm    ;            ;
          ;     Tm           *
/? are used to jump to the first occurrence of a pattern from the current cursor position:

/pattern goes forward

Latin: Lorem ipsum dolor sit amet.
*            /ips
?pattern goes backward

Latin: Lorem ipsum dolor sit amet.
?Lat             *
0$ are used to jump to the first and last character of the line.

    (whitespace)Latin: Lorem ipsum dolor sit amet.(whitespace)
    0                  *                                     $
^g_ are used to jump to the first and last printable character of the line.

    (whitespace)Latin: Lorem ipsum dolor sit amet.(whitespace)
                ^      *                         g_
Single and combined ()[]{} are used to move phrase by phrase or paragraph by paragraph or code block by code block.

<C-b> and <C-f> are used to scroll by screen backward and forward.

<C-u> and <C-d> are used to scroll by half-screen backward and forward.

H, M and L move the cursor to the top, middle, bottom of the viewport, respectively.

zt, zz and zb move the line under the cursor to the top, middle, bottom of the viewport, respectively.

And so on.

:help motion.txt will blow your mind.
```

