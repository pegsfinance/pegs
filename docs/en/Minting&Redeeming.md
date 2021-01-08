# Minting&Redeeming

Detailing the process of minting and redeeming PUSD

------

# Minting

All PUSD tokens are fungible with one another and entitled to the same proportion of collateral no matter what collateral ratio they were minted at. This system of equations describes the minting function of the Pegs cash Protocol:

<img src="http://latex.codecogs.com/svg.latex?F&space;=&space;\overbrace{\left&space;(&space;Y*P_y&space;\right&space;)}^{collateral\;value}&plus;\overbrace{\left&space;(&space;Z*P_z&space;\right&space;)}^{PEGS\;value}\hspace{222cm}" title="http://latex.codecogs.com/svg.latex?F = \overbrace{\left ( Y*P_y \right )}^{collateral\;value}+\overbrace{\left ( Z*P_z \right )}^{PEGS\;value}" />

<img src="http://latex.codecogs.com/svg.latex?\left&space;(&space;1-C_r\right&space;)\left&space;(Y*P_y\right&space;)=C_r\left&space;(&space;Z*P_z&space;\right&space;)\hspace{222cm}" title="http://latex.codecogs.com/svg.latex?\left ( 1-C_r\right )\left (Y*P_y\right )=C_r\left ( Z*P_z \right )" />

F is the units of newly minted PUSD 

C_r is the collateral ratio 

Y is the units of collateral transferred to the system 

P_y is the price in USD of $Y$ collateral 

Z is the units of PEGS burned 

P_Z is the price in USD of PEGS

**Example A: Minting PUSD at a collateral ratio of 100% with 200 USDC ($1/USDC price)** 

To be explicit, we can start by finding the PEGS needed to mint PUSD with `200 USDC` (`$1/USDC`) at a collateral ratio of 1.00

<img src="http://latex.codecogs.com/svg.latex?\left&space;(1-1.00\right&space;)\left&space;(&space;100*1.00&space;\right&space;)=1.00\left&space;(&space;Z*P_z&space;\right&space;)" title="http://latex.codecogs.com/svg.latex?\left (1-1.00\right )\left ( 100*1.00 \right )=1.00\left ( Z*P_z \right )" />

<img src="http://latex.codecogs.com/svg.latex?0=\left&space;(Z*P_z&space;\right&space;)" title="http://latex.codecogs.com/svg.latex?0=\left (Z*P_z \right )" />

Thus, we show that no PEGS is needed to mint PUSD when the protocol collateral ratio is 100% (fully collateralized). Next, we solve for how much PUSD we will get with the `200 USDC`.

<img src="http://latex.codecogs.com/svg.latex?F=\left&space;(&space;200*1.00&space;\right&space;)&plus;\left&space;(&space;0&space;\right&space;)" title="http://latex.codecogs.com/svg.latex?F=\left ( 200*1.00 \right )+\left ( 0 \right )" />

<img src="http://latex.codecogs.com/svg.latex?F=200" title="http://latex.codecogs.com/svg.latex?F=200" />

`200 PUSD` are minted in this scenario. Notice how the entire value of PUSD is in dollar value of the collateral when the ratio is at `100%`. Any amount of PEGS attempting to be burned to mint PUSD is returned to the user because the second part of the equation cancels to `0` regardless of the value of $Z$ and $P_z$.  

**Example B: Minting PUSD at a collateral ratio of 80% with 120 USDC (\$1/USDC price) and an PEGS price of $2/PEGS.**

First, we need to figure out how much PEGS, we need to match the corresponding amount of USDC.

<img src="http://latex.codecogs.com/svg.latex?\left&space;(&space;1-0.8\right&space;)\left&space;(120*1.00&space;\right&space;)=0.8\left&space;(&space;Z*2.00&space;\right&space;)" title="http://latex.codecogs.com/svg.latex?\left ( 1-0.8\right )\left (120*1.00 \right )=0.8\left ( Z*2.00 \right )" />

<img src="http://latex.codecogs.com/svg.latex?Z=15" title="http://latex.codecogs.com/svg.latex?Z=15" />

Thus, we need to deposit `15 PEGS` alongside `120 USDC` at these conditions. Next, we compute how much PUSD we will get.

<img src="http://latex.codecogs.com/svg.latex?F=\left&space;(&space;120*1.00&space;\right&space;)&plus;\left(&space;15*2.00\right&space;)" title="http://latex.codecogs.com/svg.latex?F=\left ( 120*1.00 \right )+\left( 15*2.00\right )" />

<img src="http://latex.codecogs.com/svg.latex?F=150" title="http://latex.codecogs.com/svg.latex?F=150" />

`150 PUSD` are minted in this scenario. `120 PUSD` are backed by the value of USDC as collateral while the remaining `30PUSD`  are not backed by anything. Instead, PEGS is burned and removed from circulation proportional to the value of minted algorithmic PUSD. 

**Example C: Minting PUSD at a collateral ratio of 50% with 220 USDC (\$.9995/USDC price) and an FXS price of $3.50/PEGS**

First, we start off by finding the PEGS needed.

<img src="http://latex.codecogs.com/svg.latex?\left&space;(1-0.50\right&space;)\left&space;(&space;220*0.9995&space;\right&space;)=0.50(Z*3.50)" title="http://latex.codecogs.com/svg.latex?\left (1-0.50\right )\left ( 220*0.9995 \right )=0.50(Z*3.50)" />

<img src="http://latex.codecogs.com/svg.latex?Z=62.54" title="http://latex.codecogs.com/svg.latex?Z=62.54" />

Next, we compute how much PUSD we will get.

<img src="http://latex.codecogs.com/svg.latex?F=\left&space;(&space;220*0.9995&space;\right&space;)&plus;\left&space;(&space;62.54*3.50&space;\right&space;)" title="http://latex.codecogs.com/svg.latex?F=\left ( 220*0.9995 \right )+\left ( 62.54*3.50 \right )" />

<img src="http://latex.codecogs.com/svg.latex?F=437.78" title="http://latex.codecogs.com/svg.latex?F=437.78" />

`437.78 PUSD` are minted in this scenario. Proportionally, half of the newly minted PUSD are backed by the value of USDC as collateral while the remaining 50% of PUSD are not backed by anything. `62.54 FXS` is burned and removed from circulation, half the value of the newly minted PUSD. Notice that the price of the collateral affects how many PUSD can be minted – PUSD is pegged to 1 USD, not 1 unit of USDC. 

If not enough PEGS is put into the minting function alongside the collateral, the transaction will fail with a `subtraction underflow` error.

# Redeeming

Redeeming PUSD is done by rearranging the previous system of equations for simplicity, and solving for the units of collateral, Y, and the units of PEGS, Z.

<img src="http://latex.codecogs.com/svg.latex?Y&space;=&space;\frac{F*(C_r)}{P_y}\hspace{163cm}" title="http://latex.codecogs.com/svg.latex?Y = \frac{F*(C_r)}{P_y}\hspace{163cm}" />

<img src="http://latex.codecogs.com/svg.latex?Z&space;=&space;\frac{F*(1-C_r)}{P_z}\hspace{163cm}" title="http://latex.codecogs.com/svg.latex?Z = \frac{F*(1-C_r)}{P_z}\hspace{163cm}" />

F   is the units of PUSD redeemed

C_r is the collateral ratio 

Y  is the units of collateral transferred to the user

P_y is the price in USD of $Y$collateral

Z   is the units of PEGS minted to the user 

P_z is the price in USD of PEGS

**Example D: Redeeming 170 PUSD at a collateral ratio of 65%. Oracle price is \$1.00/USDC and $3.75/PEGS.**

<img src="http://latex.codecogs.com/svg.latex?Y&space;=&space;\frac{170*(0.65)}{1.00}\hspace{163cm}" title="http://latex.codecogs.com/svg.latex?Y = \frac{170*(0.65)}{1.00}\hspace{163cm}" />

<img src="http://latex.codecogs.com/svg.latex?Y&space;=&space;\frac{170*(0.35)}{3.75}\hspace{163cm}" title="http://latex.codecogs.com/svg.latex?Y = \frac{170*(0.35)}{3.75}\hspace{163cm}" />

Thus, Y=110.5$ and Z=15.867$

Redeeming `170 PUSD` returns `$170` of value to the redeemer in `110.5 USDC` from the collateral pool and `15.867 of newly minted PEGS` tokens at the current PEGS market price.

# **minting and redemption fee**

These examples do not account for the minting and redemption fee, which are set to 0.3%,the seigniorage tax and redemption tax will be used as the fund reserve of Buyback, and 70% will flow into the dividend pool in PUSD. Staking PEGS to the dividend pool can be used for dividends, and dividends are issued every day at 0:00 UTC.

