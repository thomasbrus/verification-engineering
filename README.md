# Verification Engineering

## Instructies

Symlink mcrl22lps en lpsxsim naar ./bin:

    mkdir -p bin
    ln -s /Applications/mCRL2/Applications/mcrl22lps bin/mcrl22lps
    ln -s /Applications/mCRL2/Applications/lpsxsim.app/Contents/MacOS/lpsxsim bin/lpsxsim

Voer dan dit uit om mcrl2 te compileren:

    ./bin/mcrl22lps traveller.mcrl2 traveller.lps

En dit om de simulatie te starten:

    ./bin/lpsxsim traveller.lps
