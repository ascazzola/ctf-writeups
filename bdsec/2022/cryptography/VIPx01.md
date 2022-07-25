# VIPx01 

### 25 Points

## Information

My friend gave me his game username and game id . Can decode game id ?

    User : rot

    Game ID : OQFRP{pelcg0_ne3_nj3f0z3}

Flag Format : BDSEC{s0m3thing_here} 

## Steps done

1. We identifed the encoding using this online tool https://www.dcode.fr/cipher-identifier
2. The GAME ID was encoded using <a href="https://en.wikipedia.org/wiki/Affine_cipher">Affine Cipher</a>. We decode it using https://www.dcode.fr/affine-cipher 
3. We obtained the flag `BDSEC{crypt0_ar3_aw3s0m3}`
