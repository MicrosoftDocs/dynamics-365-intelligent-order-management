The document describes FinOps(Finance and Operations) integration solution and scenarios with Microsoft Dynamics Intelligent Order Management.

Prerequisite: You will need to set up FinOps as a provider and DualWrite enabled in Dataverse and Intelligent Order Management. Follow the instructions in [Set up the Dynamics 365 Finance + Operations provider](set-up-finops-provider.md) in Dynamics 365 Intelligent Order Management.


FinOps Integration solution:
The following steps describe the FinOps high level solution for integration with Intelligent Order Management.

1.  Intelligent Order Management will use DualWrite for data sync between FinOps and Intelligent Order Management.
2.  Ecommerce orders will be coming into Intelligent Order Management without company code. Company code will be assigned using a policy before synchin to FinOps.
3.  FinOps provider action will send over order from Intelligent Order Management to FinOps fulfillment or billing when order is ready to sync. 
4.  The FinOps data assignment policy and provider actions will be called in designed orchestration flow.
5.  FinOps order status event handler is introduced to monitor and raise business events in Intelligent Order Management when the order status is updated in FinOps.
    
FinOps provider integration scenarios with Intelligent Order Management:
The following scenarios describe the FinOps integration scenarios with Intelligent Order Management.

1.	BigCommerce (new Order) -> Intelligent Order Management -> FinOps (fulfillment) -> FinOps (accounting)

  a.	Order created in BigCommerce
  b.	Order pulled into Intelligent Order Management from BigCommerce
  c.	Order validated in Intelligent Order Management
  d.	Company, site and warehouse assigned in Intelligent Order Management
  e.	Order sent to FinOps by FinOps provider action
         i.	Order sent to fulfillment successful event raised in Intelligent Order Management
  g.	Order shipped in FinOps
         i.  Order shipped event raised in Intelligent Order Management
         ii. Order status updated in BigCommerce by provider action
  h.	Order invoiced in FinOps
         i.  Order invoiced event raised in Intelligent Order Management
         ii. Order status updated in BigCommerce by provider action

2.  BigCommerce(new order)->Intelligent Order Management->Flexe(fulfillment)->FinOps(accounting)

  a.    Order created in BigCommerce
  b.    Order pulled into Intelligent Order Management from BigCommerce
  c.    Order validated in Intelligent Order Management
  d.    Order sent to Flexe for fulfillment by Flexe provider action
  e.    Order shipped by Flexe
  f.    Assgn site warehoues and company in Intelligent Order Management order
  g.    Order sent to FinOps by FinOps Provider action
  h.    Order invoiced in FinOps
  i.     Order invoiced event raised in Intelligent Order Management.
  j.    Order status updated in BigCommerce by provider action


3.  FinOps(new order) -> Intelligent Order Management -> Flexe(fulfillment) -> FinOps(accounting)

  a.    Order created in FinOps
  b.    FinOps order sent to Intelligent Order Management by DualWrite
  c.    Order confirmed in FinOps
  c.    Order validated in Intelligent Order Management
  d.    Order sent to Flexe for fulfillment by Flexe provider action
  e.    Order shipped by Flexe
  f.    Order status update sent to FinOps by FinOps provider action
  g.    Order invoiced in FinOps
  i.    Order invoiced event raised in Intelligent Order Management

4.  FinOps(new order)->Intelligent Order Management->FinOps(fulfillment)->FinOps(accounting)

  a.    Order created in FinOps
  b.    FinOps order sent to Intelligent Order Management by DualWrite
  c.    Order confirmed in FinOps
  d.    Order validated in Intelligent Order Management
  e.    Order shipped in FinOps
         i.  Order shipped event raised in Intelligent Order Management
  f.    Order invoiced in FinOps
         i.  Order invoiced event received in Intelligent Order Management

5.  FinOps(new order)->Intelligent Order Management->Flexe(fuflillment)->SAP(accounting)
   a.   Order created in FinOps
   b.   FinOps order sent to Intelligent Order Management by DualWrite
   c.   Order confirmed in FinOps
   d.   Order validated in Intelligent Order Management
   e.   Order sent to Flexe for fulfillment by provider action
   f.   Order shipped event raised in Intelligent Order Management
   g.   Order invoiced in SAP
   h.   Order invoiced event received in Intelligent Order Management
