# wiki-corpora-generator

A script that generates corpora (preferably for further exploration/exploiation
in context of Natural Language Processing) by dumping text from rendered
Wikipedia pages and traversing pages they point to using Breath First Search.

The process of dumping goes as follows:

1. The article/page specified in `--title` added to a Queue.

2. The first article/page title from Queue is taken. It is then dumped and if
   it contains links to other pages (that is those that were not visited yet)
   these are added to a Queue.

3. Part 2. is repeated until the Queue is not empty or the `--limit` of
   articles/pages has not been reached.


Note that this script does not only work on `en.wikipedia.org` but also on any
other Wikipedia locale. The language can be specified with the `--lang`
parameter.

This can be useful when generating a corpora on a given topic (and possibly in
different languages).

## Example

        $ python wikicg.py --title 'Artificial intelligence' --count 10
        Dumped (10) <WikipediaPage 'Artificial intelligence'>
        Dumped (9) <WikipediaPage '2001: A Space Odyssey'>
        Dumped (8) <WikipediaPage '3D optical data storage'>
        Dumped (7) <WikipediaPage '3D printing'>
        Dumped (6) <WikipediaPage '613 commandments'>
        Dumped (5) <WikipediaPage 'Chester A. Arthur'>
        Dumped (4) <WikipediaPage 'A.I. Artificial Intelligence'>
        Dumped (3) <WikipediaPage 'ACM Computing Classification System'>
        Dumped (2) <WikipediaPage 'Artificial intelligence'>
        Dumped (1) <WikipediaPage 'AI-complete'>


        $ python wikicg.py --title 'Inteligencia artificial' --count 10 --lang es
        Dumped (10) <WikipediaPage 'Inteligencia artificial'>
        Dumped (9) <WikipediaPage '2001: A Space Odyssey (novela)'>
        Dumped (8) <WikipediaPage '2001: A Space Odyssey (película)'>
        Dumped (7) <WikipediaPage 'Agente inteligente (inteligencia artificial)'>
        Dumped (6) <WikipediaPage 'Ajedrez'>
        Dumped (5) <WikipediaPage 'Alan Kay'>
        Dumped (4) <WikipediaPage 'Alan Turing'>
        Dumped (3) <WikipediaPage 'Alex Garland'>
        Dumped (2) <WikipediaPage 'Algoritmo genético'>
        Dumped (1) <WikipediaPage 'Alicia Vikander'>
