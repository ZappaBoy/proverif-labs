
# Table of Contents

1.  [Esercizio 1](#org6818fc2)
    1.  [Denning-sacco](#org7148caa)



<a id="org6818fc2"></a>

# Esercizio 1


<a id="org7148caa"></a>

## Denning-sacco

    Initial clauses:
    Clause 11: c:c[]
    Clause 10: c:pk(sA[])
    Clause 9: c:pk(sB[])
    Clause 8: c:x & c:encrypt(m,pk(x)) -> c:m
    Clause 7: c:x -> c:pk(x)
    Clause 6: c:x & c:y -> c:encrypt(x,y)
    Clause 5: c:sign(x,y) -> c:x
    Clause 4: c:x & c:y -> c:sign(x,y)
    Clause 3: c:pk(x) -> c:encrypt(sign(k[pk(x)],sA[]),pk(x))
    Clause 2: c:encrypt(sign(k_1,sA[]),pk(sB[])) -> c:encrypt(secret[],pk(k_1))
    Clause 1: c:new-name[!att = v]
    Completing...
    goal reachable: c:secret[]
    
    Derivation:
    Abbreviations:
    k_1 = k[pk(x)]
    clause 8 c:secret[]
        clause 5 c:k_1
            duplicate c:sign(k_1,sA[])
        clause 2 c:encrypt(secret[],pk(k_1))
            clause 6 c:encrypt(sign(k_1,sA[]),pk(sB[]))
                clause 8 c:sign(k_1,sA[])
                    duplicate c:x
                    clause 3 c:encrypt(sign(k_1,sA[]),pk(x))
                        clause 7 c:pk(x)
                            any c:x
                clause 9 c:pk(sB[])
    RESULT goal reachable: c:secret[]

