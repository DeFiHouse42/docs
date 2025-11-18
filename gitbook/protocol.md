# 🏗 The DeFi House Protocol  
_Fixed-term, fixed-rate, over-collateralized P2P lending_

> [!IMPORTANT]  
> **Status:**  
> - Protocol is in the **design & planning phase**  
> - MVP development will begin after the DFH token launch  
> - MVP will deploy on **BNB Chain**  

---

# 🎯 Design Philosophy

The protocol is built upon these core principles:

<div style="color:#2aff80;font-weight:600">1. Predictability</div>  
Borrowers should know exactly what they owe and when.

<div style="color:#2aff80;font-weight:600">2. No Liquidations Mid-Term</div>  
Collateral remains locked for the loan duration; no price-triggered liquidations.

<div style="color:#2aff80;font-weight:600">3. Lender-Defined Terms</div>  
Lenders choose:
- Interest rate  
- Duration  
- Collateral requirements  
- Assets they accept  

<div style="color:#2aff80;font-weight:600">4. Responsible Risk Framework</div>  
Over-collateralization protects lenders.  
Defaults are simple: lender receives the collateral.

<div style="color:#2aff80;font-weight:600">5. Simplicity</div>  
Straightforward UX for both borrowers and lenders.

---

# 🔄 Loan Lifecycle

## 1. Lender Creates Offer
Lender defines:
- Rate  
- Duration  
- Loan size  
- Accepted collateral  
- LTV  

Offer is published on-chain.

## 2. Borrower Matches Offer
Borrower deposits collateral → receives loan principal.

## 3. Loan Term
- No liquidations  
- Fixed rate  
- Borrower may repay early (with possible fee)

## 4. Maturity
- Borrower repays full amount → receives collateral  
- Or defaults → lender receives collateral  

---

# 🔐 Collateral & Risk Management

> [!INFO]  
> **MVP collateral will be conservative.**

Likely candidates:
- BNB  
- Stablecoins  
- ETH/Blue-chip L1 assets  
- Liquid staking tokens (subject to risk analysis)

Future additions:
- LP tokens  
- Yield-bearing collateral  
- Cross-chain collateral with messaging guarantees  

---

# 🔗 Cross-Chain Vision (Future)

The protocol aims to become a **cross-chain credit network**:

Borrower on Chain B → Collateral on Chain B  
Lender on Chain A → Capital on Chain A  

> [!WARNING]  
> This is a **future phase** and requires careful security analysis.

Benefits:
- Unify fragmented liquidity  
- Chain-agnostic credit history  
- Better matching surface  
- Efficient capital utilization  
