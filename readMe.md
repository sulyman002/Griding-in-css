/* 
I notice for the project i want to learn am going to need a bunch of class name, which may cause me to run into specisifity problem in css.

So to get rid of that, i want to learn how to use @layer  in css. which is sub-divided into three.
user agent styles
user styles
author styles (This the only one we have access to).
     This author styles is the one with the most high specitifity and its also sub divideinto four 4
reset
base
layout
components

N.B: this author do/make its specitifity based on the on that come first 
Example: 
@layer components{
    .box{
         font-size: 15px;
     }
}

@layer reset{
    .box{
         font-size: 15px;
     }
}


For this type of situation, the RESET own will be more of high specitifity.

TO GET RID OF THESE, like to set the specitifity to our own taste, 
we can do it like this

@layer framework, reset, base, layout, components, utilities;

*/


* {

    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "DM Sans", sans-serif;
    line-height: 1.1;
}

body {
    margin: 30px;
    background-color: rgb(241, 230, 230);
}

:root {
    /* Color Variables */
    --purple-100: hsl(254, 88%, 90%);
    --purple-500: hsl(256, 67%, 59%);

    --Yellow-100: hsl(31, 66%, 93%);
    --Yellow-500: hsl(39, 100%, 71%);

    --white: hsl(0, 0%, 100%);
    --black: hsl(0, 0%, 0%);

    /* Font Variables */

    --fs-sm: 1.125rem;
    --fs-md: 2.25rem;
    --fs-xl: 3rem;
    --fs-xxl: 4rem;

    /* Font Weight Variables */
    --fw-light: 300;
    --fw-regular: 400;
    --fw-bold: 500;

    /* General reset */

}

/* @layer reset {

    h1,
    h2 {
        margin: 0;
        color: var(--cards-tittle-color, #fff);
        ;
        font-weight: var(--fw-bold);
        font-size: var(--cards-heading-size, var(--fs-md));
        text-wrap: balanced;

    }

    img {
        max-width: 100%;
        display: block;
    }




    
} */

h1, h2 {
  margin: 0;
  color: var(--cards-tittle-color, #fff);
  font-weight: var(--fw-bold);
  font-size: var(--cards-heading-size, var(--fs-md));
  text-wrap: balanced;
}

img {
  max-width: 100%;
  display: block;
}

/* @layer layout { */
.card_container {
    display: grid;
    gap: 1.5rem;
    background-color: rgb(241, 234, 234);

    grid-template-areas:
        "one"
        "two"
        "three"
        "four"
        "five"
        "six"
        "seven"
        "eight";

    
}

.card_container>* {
    display: grid;
    background-color: var(--background-cards-color, grey);
    gap: var(--cards-spacing, 1.875rem);
    padding: var(--cards-padding, 1.875rem);
    border-radius: var(--cards-border-radius, 1.25rem);
    justify-items: var(--cards-horizontal-alignment, center);
    align-items: var(--cards-vertical-alignment, center);
    text-align: var(--cards-horizontal-alignment, center);
    color: var(--cards-text-color, #fff);

    p {
        font-size: var(--Ps-cards-fs, 1rem);
    }


}


.card_container img {
    max-width: var(--cards-image-max-width, 100%);
    width: var(--cards-image-max-width, 100%);
}



.cards:nth-child(1) {
    --cards-image-max-width: 60%;
    --cards-heading-size: var(--fs-xxl);
    --background-cards-color: var(--purple-500);
    grid-area: one;

    span {
        color: var(--Yellow-500);
        font-style: italic;
    }
}

.cards:nth-child(2) {
    --background-cards-color: var(--white);
    --cards-tittle-color: var(--black);
    --cards-horizontal-alignment: left;
    grid-area: two;

    img {
        order: -1;
        --cards-image-max-width: 100%;
        filter: drop-shadow(0 0 1rem rgba(0, 0, 0, 0.3));
        border-radius: 100vw;


    }
}

.cards:nth-child(3) {
    overflow: hidden;
    --cards-horizontal-alignment: left;
    --background-cards-color: var(--Yellow-500);
    --cards-tittle-color: var(--black);
    grid-area: three;

    img {
        margin-bottom: -70px;
    }
}



.cards:nth-child(4) {
    --background-cards-color: var(--purple-100);
    --cards-tittle-color: var(--black);
    --cards-text-color: var(--black);
    grid-area: four;
    text-wrap: balanced;
}

.cards:nth-child(5) {
    --background-cards-color: var(--purple-500);
    --cards-tittle-color: var(--white);
    grid-area: five;

    img {
        --cards-image-max-width: 85%;

    }
}

.cards:nth-child(6) {
    --background-cards-color: var(--white);
    --cards-tittle-color: var(--black);
    --cards-text-color: var(--black);
    --cards-horizontal-alignment: left;
    --Ps-cards-fs: 1.7rem;
    --cards-image-max-width: 65%;
    grid-area: six;


}


.cards:nth-child(7) {
    --background-cards-color: var(--Yellow-100);
    --cards-tittle-color: var(--black);
    --cards-horizontal-alignment: left;
    --cards-image-max-width: 55%;
    --cards-image-max-width: 60%;
    --cards-padding: 2rem;
    grid-area: seven;

    span {
        color: var(--purple-500);
        font-style: italic;
    }
}

.cards:nth-child(8) {
    --background-cards-color: var(--Yellow-500);
    --cards-tittle-color: var(--black);
    --cards-text-color: var(--black);
    --cards-horizontal-alignment: left;
    --Ps-cards-fs: 1.7rem;
    --cards-image-max-width: 75%;
    text-wrap: wrap;
    grid-area: eight;
    --cards-heading-size: var(--fs-xl);

}







@media screen and (min-width: 960px) {
    .card_container {
        grid-template-columns: 1fr 1fr 1fr 1fr;
        grid-template-areas:
            "six one one four"
            "six two three four"
            "eight two three four"
            "eight six five five";
    }
}




/* @media screen and (max-width: 375px) {

    
}
@media screen and (max-width: 764px) {

    
}*/

/* @media screen and (max-width: 1024px) {
    body {
        background-color: red;
    }

    .card_container {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        grid-template-areas: "six one one four"
            "six two three four"
            "eight two three four"
            "eight six five five";
    }

} */

/* @media screen and (max-width: 1440px) {

    
}  */