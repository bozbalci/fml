# to-do
Keeping track of tasks

### piano.csv

List of the piano concertos I'd like to listen to.

Format:

    composer,title,listened
    Rachmaninoff,"Piano Concerto No. 2",yes
    Rachmaninoff,"Piano Concerto No. 3",yes
    Rachmaninoff,"Piano Concerto No. 4",no

Commands:

    $ awk -F, '/Rachmaninoff/ {if ($3 == "yes") print $2}' piano.csv | tr -d \" 
    Piano Concerto No. 2
    Piano Concerto No. 3
