## vim cheats

### references
https://danielmiessler.com/study/vim/
https://devhints.io/vim
https://www.reddit.com/r/vim/comments/32r85c/this_is_my_favorite_vim_cheat_sheet_does_anyone/


### vimrc file

### examples
d2w = delete 2 words\
cis = change inside sentence\
yip = yank inside paragraph\
ct[ = change to left bracket\
cf[ = change up to and including left bracket

### verbs
d = delete\
c = change\
y = yank\
v = visually select\
0 = start of line\
$ = end of line\
w = forward one word\
b = back one word\
e = end of word\
H = hight (top of screen)\
M = middle\
L = low (bottom of screen)

### adverbs
f = find (stop on character)\
t = to (stop before character)\
/ = find string\
i = inside\
a = around\
NUM = number (a number of positions)

### nouns
w = word\
s = sentence\
p = paragraph\
b = block

### other
ZZ = :wq\
:saveas = save as\
/[string] = search for string\
  n = next occurence of string\
  N = previous occurence of string

### copy
y #yank\
yy #yank line

#### cut
dd #cut (delete) line

#### paste
p\
P #paste before

#### delete
d\
dd #cut (delete) line

#### find
/\
n #next

#### undo
u\
<C-R> #redo

#### start of line
0

#### end of line
$

#### append after line
o #start new line and enter insert mode

#### search and replace

:% s/[search_string]/[replacement_string]/g  
  #% = entrire file, g = global (all occurences on a single line, not just the first)
  
5,10 s/[search_string]/[replacement_string]/g
  #5,10 = lines 5 to 10, g = global (all occurences on a single line, not just the first)
