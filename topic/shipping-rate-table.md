
# Shipping rate factor table 

As part of April 2023 release, Shipping rate factor table is now available within Dynamics 365 Intelligent Order Management.
This table allows for the configuration of rate mark ups, static rates and increments based on weight thresholds for different carrier service levels.
The rate factor table represents as a fall back option when either carrier rate API fails or when dynamic rate APIs are not available for a carrier.

## Description of fields within shipping rate factor table

1. **Name** - Name or description of the carrier service.
2. **Fulfilment source type**- This points to the **Fulfilment source type** in **Fulfilment settings**. For example if a store and distribution center could have different carrier services offered with different rates.
3. **Address type** - This describes the destination address type if it is **Business** or **Residence**.
4. **Rate factor** - This describes a mark up or down of the calculated rate from the carrier API if applicable.
5. **Free shipping** - This describes a flag whether the service is applicable for free shipping.
6. **Fallback weight threshold** - This describes weight threshold for which a static rate would be defined.
7. **Fallback rate** - This describes a static rate until weight threshold.
8. **Fallback increment rate factor** - This describes a rate factor applied for incremental weight over threshold. 
 (For example if weight threshold is 5lbs and a static rate is $8 and increment rate factor is 0.75, and if the total weight of the order is 10lbs - the rate would be calculated as 8+0.75*5 =11.75)

## Using the shipping rate factor table in Intelligent Order Management DOM(Distributed Order Management) API.
Intelligent Order Management DOM API calls the Fedex rate API to calculate the shipping rate. IF shipping rate could not be calculated
for some reason due to the API issues, a fall back rate is calculate using the **fall back weight threshold** and the **fall back increment rate factor** defined for each service levels in the table.
If the carrier API returns a valid rate, a mark up/down percentage is applied from the **rate factor** percentage maintained in the table.





