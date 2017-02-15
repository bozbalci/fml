# to-do
Things on my to-do list.

### piano-concertos

List of the piano concertos I'd like to listen to.

Syntax:

    Composer:Title of work:Listened

e.g.

    Saint-Saens:Piano Concerto No. 5:yes

Example command(s):

    $ gawk -F: '/Mozart/ {print $2}' piano-concertos
    Piano Concerto No. 7
    Piano Concerto No. 9
    Piano Concerto No. 20
    Piano Concerto No. 22
    Piano Concerto No. 23
    Piano Concerto No. 24
    Piano Concerto No. 25
    Piano Concerto No. 27

    $ gawk -F: -i inplace '' piano-concertos
