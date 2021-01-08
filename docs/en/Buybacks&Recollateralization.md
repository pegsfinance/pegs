# Buybacks & Recollateralization



The protocol at times will have excess collateral value or require adding collateral to reach the collateral ratio. To quickly redistribute value back to PEGS holders or increase system collateral, two special swap functions are built into the protocol: buyback and recollateralize. 

# Recollateralization

Anyone can call the recollateralize function which then checks if the total collateral value in USD across the system is below the current collateral ratio. If it is, then the system allows the caller to add up to the amount needed to reach the target collateral ratio in exchange for newly minted PEGS at a bonus rate. The bonus rate is set to `0.75%` to quickly incentivize arbitragers to close the gap and recollateralize the protocol to the target ratio. The bonus rate can be adjusted or changed to a dynamic PID controller adjusted variable through governance. 
$$
PEGS_{received}= \frac{(Y∗P_y)(1+B_r)}{P_z}\hspace{222cm}
$$
$Y$ is the units of collateral needed to reach the collateral ratio 

$P_y$ is the price in USD of $Y$ collateral 

$B_r$ is the bonus rate for PEGS emitted when recollateralizing 

$P_z$ is the price in USD of PEGS

**Example A: There is 100,000,000 PUSD in circulation at a 50% collateral ratio. The total value of collateral across the USDT and USDC pools is 50m USD and the system is balanced. The price of PUSD drops to $0.99 and the protocol increases the collateral ratio to 50.25%.**

There is now `$250,000` worth of collateral needed to reach the target ratio. Anyone can call the recollateralize function and place up to $250,000 of collateral into pools to receive an equal value of PEGS plus a bonus rate of `0.75%`. 

Placing `250,000 USDT` at a price of `$1.00/USDT` and a market price of `$3.80/PEGS` is as follows:
$$
PEGS_{received}= \frac{(250000∗1.00)(1+0.0075)}{3.80}\hspace{222cm}
$$

$$
PEGS_{received}= 66282.89\hspace{222cm}
$$

# Buybacks

The opposite scenario occurs when there is excess collateral in the system than required to hold the target collateral ratio. This can happen a number of ways: 

- The protocol has been lowering the collateral ratio successfully keeping the price of PUSD stable
- Interest bearing collateral is accepted into the protocol and its value accrues
- Minting and redemption fees are creating revenue

In such a scenario, any PEGS holder can call the buyback function to exchange the amount of excess collateral value in the system for PEGS which is then burned by the protocol. This effectively redistributes any excess value back to the PEGS distribution and holders don't need to actively participate in buybacks to gain value since there is no bonus rate for the buyback function. It effectively models a share buyback to the governance token distribution. 
$$
Collateral_{received}=\frac{Z*P_z}{P_z}\hspace{222cm}
$$
$Z$ is units of PEGS deposited to be burned 

$P_y$ is the price in USD of the collateral 

$P_z$ is the price in USD of PEGS

**Example B: There is 150,000,000 PUSD in circulation at a 50% collateral ratio. The total value of collateral across the USDT and USDC pools is 76m USD. There is $1m worth of excess collateral available for PEGS buybacks.**

Anyone can call the buyback function and burn up to `$1,000,000 worth of PEGS` to receive excess collateral.

Burning `238,095.238 PEGS` at a price of `$4.20/PEGS` to receive USDC at a price of `$0.99/USDC` is as follows:
$$
USDC_{received}=\frac{238095.238*4.20}{0.99}\hspace{222cm}
$$

$$
USDC_{received}= 1010101.01\hspace{222cm}
$$

