#  Find Me Inside

### 50 Points

## Information

I'm stuck in the Dark.

Attachments

    fireflies.gif

Download Links:

 1. <a href="https://drive.google.com/drive/folders/1iqw_9aZk-1tiv6EK4xNT6m5yfPbpXW0y?usp=sharing">Link 1 </a>
 2. <a href="https://drive.google.com/drive/folders/1pz__cKtaR2zGI4AKjq8rmA2Sz0JSONHv?usp=sharing">Link 2 </a>
 3. <a href="https://drive.google.com/drive/folders/17IYk-A30Y83AkrCC5PfAnFdjfpO71RnK?usp=sharing">Link 3 </a>

Flag Format : BDSEC{flag_here}

## Steps done

1. We downloaded the image
2. We run binwalk -e fireflies.gif
3. A file was extracted called cry100
4. We opened the file with a text editor and the content is 
    
        Sld xlfow R yv hl olhg
        Rm z kozxv R pmld hl dvoo?
        Sld xlfow R yv hl yilpvm
        Rm z uznrob hl gltvgsvi?
        Sld xlfow R yv hl olmvob
        Hfiilfmwvw yb hl nzmb?
        Sld xlfow R yv hl fmszkkb
        Hfiilfmwvw yb hl nfxs yvzfgb?
        Sld xlfow R yv nv
        Dsvm vevm R ivnzrm z nbhgvib?
        YWHVX{N33n_gsv_yfggviuob_tlvh_fk_fk_zmw_zdzb}
5. We analyzed the text with this online tool https://www.dcode.fr/cipher-identifier
6. The result was Atbash cipher and we extract the text:

        How could I be so lost
        In a place I know so well?
        How could I be so broken
        In a family so together?
        How could I be so lonely
        Surrounded by so many?
        How could I be so unhappy
        Surrounded by so much beauty?
        How could I be me
        When even I remain a mystery?
        BDSEC{M33m_the_butterfly_goes_up_up_and_away}
7. Finally the flag is `BDSEC{M33m_the_butterfly_goes_up_up_and_away}`