# Basically RSA

### 100 Points

## Information

RSA cryptosystem uses modular arithmetic to create an asymmetric encryption system. However, there are some pitfalls and weakness. Can you exploit it?

    N: 1280678415822214057864524798453297819181910621573945477544758171055968245116423923

    E: 65537

    C: 241757357533719849989659127349827982677055294256023833052829147857534659015212862

Flag Format : BDSEC{fl4g_h3r3}

## Steps done

1. The clue here is we know the value of the parameter `N`. `N` and `P` must be secret to ensure the security of RSA.
2. We visited this url https://www.dcode.fr/rsa-cipher 
3. We filled the parameters and we get the flag `BDSEC{r54_i5_fUn_r16h7?}`
