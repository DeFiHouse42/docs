# Loan Mechanics

The protocol follows a **simple lifecycle** designed to *maximize clarity*.

## Lender Offer Creation
Lenders define:
- **Loan asset**  
- **Principal amount**  
- **Duration**  
- **Fixed interest**  
- **Required collateral ratio**  
- **Accepted collateral types**  

Offers are published in an **on-chain registry**.

## Borrower Match
Borrowers select an offer and deposit collateral.  
Upon confirmation:
- Collateral is **locked**  
- Loan principal is **released**  
- A **fixed maturity date** is set  

## During the Loan
- **No liquidations**  
- Collateral remains **locked**  
- *Optional early repayment* (if implemented)

## Settlement
At maturity:
- Borrower repays **principal + interest** → *collateral is returned*  
- If **no repayment** → *lender claims collateral*  

## Collateral & Risk

### Initial Collateral Types
MVP collateral will be **conservative**:
- **BNB**  
- **Stablecoins**  
- *Selected blue-chip assets*  

### Collateralization Ratios
Set **per asset** and *adjustable by lenders*.  
Initial parameters aim to **minimize under-collateralization risk**.

### Default Handling
Default transfers collateral to the lender as **defined in the loan terms**.
