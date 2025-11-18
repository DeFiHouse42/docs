# The DeFi House Protocol

The DeFi House protocol is a planned P2P lending marketplace focused on fixed-term, fixed-rate, over-collateralized loans with no liquidations during the loan term.

This section describes the intended design. It reflects a planning and specification phase, not a live implementation.

{% hint style="warning" %}
There is currently no deployed DeFi House lending protocol. Everything described here is subject to change based on design, audits, and market feedback.
{% endhint %}

---

## Objectives

The protocol is designed with several objectives:

- Provide a predictable borrowing experience  
- Allow lenders to define their own risk/return profile  
- Avoid unexpected liquidations during the loan term  
- Start on a single chain (BNB Chain) to reduce complexity  
- Extend, over time, to cross-chain credit and liquidity  

---

## Design Principles

### Fixed-Term and Fixed-Rate

Borrowers should know in advance:

- The principal they receive  
- The interest they will pay  
- The exact repayment date  

This allows for planning and reduces uncertainty around variable rates.

### Over-Collateralized

Loans are over-collateralized by design. Borrowers deposit more value in collateral than the loan principal they receive. This is intended to protect lenders in default scenarios.

Exact collateralization ratios will:

- Depend on the asset  
- Be conservative in early versions  
- Be configurable via parameters (set initially by the team, governed later)

### No Mid-Term Liquidations

Many DeFi lending protocols liquidate positions when collateral prices fall. In this design:

- Collateral is locked for the duration of the loan  
- There are no automated, price-triggered liquidations during the term  
- If the borrower does not repay at maturity, the lender gains access to the collateral as specified by the loan terms  

This shifts risk management from continuous monitoring to clear up-front terms and end-of-term outcomes.

### Lender-Defined Terms

Lenders can define:

- Loan currency  
- Principal amount  
- Interest rate  
- Loan duration  
- Required collateral ratio  
- Accepted collateral assets  

This allows lenders to express their own risk preferences, rather than relying on a single pooled risk model.

---

## Loan Lifecycle

The loan lifecycle is conceptually as follows.

### 1. Lender Creates an Offer

A lender specifies:

- Loan asset and amount  
- Duration (for example 7, 30, 90 days)  
- Interest rate (expressed as a fixed amount or APR)  
- Accepted collateral assets  
- Required collateralization ratio (for example 150%)  

The protocol records this as an open offer in an on-chain orderbook.

### 2. Borrower Accepts an Offer

A borrower reviews available offers and chooses one that matches their needs. To accept an offer, the borrower:

- Deposits the required collateral  
- Confirms the loan terms  

The protocol:

- Locks the collateral  
- Transfers the loan principal to the borrower  
- Records the loan as active with a known maturity date  

### 3. During the Loan

During the life of the loan:

- No price-based liquidations take place  
- The borrower may be allowed to repay early (if the design includes early repayment, this may involve a fixed penalty or fee to keep returns predictable for lenders)  

### 4. Maturity and Settlement

At or before maturity, the borrower can repay:

- Principal plus interest  

Upon full repayment:

- The protocol returns the collateral to the borrower  

If the borrower does not repay by the agreed maturity:

- The lender can claim the collateral  
- The protocol records the loan as defaulted  

The specific mechanics for default (e.g. grace periods, partial recovery) will be defined in the implementation and may evolve over time.

---

## Collateral and Risk

### Initial Collateral Types

The MVP will likely support a limited set of conservative assets as collateral, such as:

- BNB  
- Selected stablecoins  
- Possibly a limited number of blue-chip assets  

The choice of assets will be influenced by:

- Liquidity  
- Historical volatility  
- On-chain integration complexity  

### Collateral Ratios

Collateral requirements will be set with:

- A baseline minimum per asset type  
- Lender flexibility to demand higher ratios  

In early versions, collateral ratios will be intentionally conservative to reduce the risk of under-collateralization.

---

## Cross-Chain Vision (Planned)

In the long term, DeFi House aims to become a cross-chain credit network.

Conceptually, this includes:

- Lenders providing capital on one chain  
- Borrowers posting collateral and drawing liquidity on another chain  
- Synchronization of loan state across chains using secure cross-chain messaging  
- A unified reputation framework so borrower behavior on one chain is recognized elsewhere  

{% hint style="info" %}
Cross-chain loan settlement introduces additional complexity and security considerations.  
It is a future phase, not part of the MVP. Implementation will depend on the maturity and security posture of cross-chain messaging infrastructure available at that time.
{% endhint %}

---

## Future Protocol Evolution

Potential future features include:

- Support for a wider range of collateral types, including LP tokens and yield-bearing assets  
- Optional insurance pools for lenders, funded by premiums and involving DFH stakers  
- More sophisticated borrower reputation scoring  
- Refinancing and roll-over mechanisms  
- Configurable loan templates for specific use cases (for example, treasury financing for projects)  

All of these are conceptual at this stage and will depend on user demand, technical feasibility, and risk assessment.
