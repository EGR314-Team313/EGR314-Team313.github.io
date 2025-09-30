---
title: Component Selection 
---

## Subsystems

### Luke Jeffs


*Table 1: LED Array*

**Shift Register**
| **Solution**                              | **Pros**                                        | **Cons**                                      |
| ---------------------------------- | ----------------------------------------------- | ----------------------------------------------------------------- |
|     <img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/2c107a6b-1226-4e08-8c50-b11ba5555ddd" /> <br>74HC595PW-Q100,118 |-rated for high temperature<br>-inexpensive <br> -gull-wing leads|  -lower drive current <br> 
|     <img width="225" height="212" alt="image" src="https://github.com/user-attachments/assets/6223c4b3-906d-4393-9681-ddfb51335681" /> <br> TPIC6B595DWR    |   -Higher potential drain current <br> -high temperature rating   |   -Largest Footprint <br> -more expensive
|     <img width="231" height="202" alt="image" src="https://github.com/user-attachments/assets/e52301ae-f8c1-43e1-b7f3-2ecdd64cae04" /> <br> MIC5891YWM-TR   |   -Highest drain current per pin  <br> -could drive more LEDs reliably   | -Most expensive <br>-Highest supply voltage  

**Choice:** Option 1, 74HC595PW-Q100,118

**Rationale:** This choice has a significant number in stock at a low price, a very clear datasheet, and a comes in a package I can reliably solder with confidence. Many can be purchased for testing and the simplicity allows for the initial goals to be reached and further development to be explored.

### Style 2

> Also acceptable, more markdown friendly

**External Clock Module**

1. XC1259TR-ND surface mount crystal

    ![](image1.png)

    * $1/each
    * [link to product](http://www.digikey.com/product-detail/en/ECS-40.3-S-5PX-TR/XC1259TR-ND/827366)

    | Pros                                      | Cons                                                             |
    | ----------------------------------------- | ---------------------------------------------------------------- |
    | Inexpensive                               | Requires external components and support circuitry for interface |
    | Compatible with PSoC                      | Needs special PCB layout.                                        |
    | Meets surface mount constraint of project |

1. CTX936TR-ND surface mount oscillator

    ![](image3.png)

    * $1/each
    * [Link to product](http://www.digikey.com/product-detail/en/636L3I001M84320/CTX936TR-ND/2292940)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | Outputs a square wave                                             | More expensive      |
    | Stable over operating temperature                                 | Slow shipping speed |
    | Direct interface with PSoC (no external circuitry required) range |

**Choice:** Option 2: CTX936TR-ND surface mount oscillator

**Rationale:** A clock oscillator is easier to work with because it requires no external circuitry in order to interface with the PSoC. This is particularly important because we are not sure of the electrical characteristics of the PCB, which could affect the oscillation of a crystal. While the shipping speed is slow, according to the website if we order this week it will arrive within 3 weeks.
