# Verification Engineering

## Instructies

Symlink mcrl22lps en lpsxsim naar ./bin:

    mkdir -p bin
    ln -s /Applications/mCRL2/Applications/mcrl22lps bin/mcrl22lps
    ln -s /Applications/mCRL2/Applications/lpsxsim.app/Contents/MacOS/lpsxsim bin/lpsxsim

## Simulatie
Om traveller.mcrl2 te compileren naar traveller.lps gebruiken we het volgende commando:

    $ ./bin/mcrl22lps traveller.mcrl2 traveller.lps

Om vervolgens de simulatie te starten gebruiken we het commando:

    $ ./bin/lpsxsim traveller.lps


## Verificatie 

### Met pbes2bool 
Om traveller.mcrl2 te compileren naar traveller.lps gebruiken we het volgende commando:

    $ ./bin/mcrl22lps traveller.mcrl2 traveller.lps

De formele eisen checken we door lps2pbes uit te voeren:

    $ ./bin/lps2pbes traveller.lps traveller.pbes \ 
    --formula=./requirements/requirement_<x>.mcf --structured --verbose

En uiteindelijk kunnen we checken of aan de eisen is voldaan:

    $ ./bin/pbes2bool traveller.pbes --pbes-rewriter=quantifier-all \ 
    --rewriter=jitty --strategy=0 --verbose

### Met pbes2lts-sym
Om traveller.mcrl2 te compileren naar traveller.lps gebruiken we het volgende commando:

    $ ./bin/mcrl22lps -vfDn traveller.mcrl2 traveler.lps

De formele eisen checken we door lps2pbes uit te voeren:

    $ ./bin/lps2pbes -s -frequirements/requirement_<x>.mcf traveler.lps \
    traveller.pbes 

En uiteindelijk kunnen we checken of aan de eisen is voldaan:

    $ ./bin/pbes2lts-sym --pg-solve -rgs traveller.pbes