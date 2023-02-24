---
title: AI simulations feature
description: This article provides an overview of the AI simulations feature in Microsoft Dynamics 365 Intelligent Order Management.
ms.date: 01/25/2023
author: derekkwanpm
ms.author: derekkwan
ms.topic: conceptual
ms.custom: bap-template
---

# AI simulations feature

[!include [banner](includes/banner.md)]

This article provides an overview of the artificial intelligence (AI) simulations feature in Microsoft Dynamics 365 Intelligent Order Management.

> [!NOTE]
> The AI simulations feature is currently in development. If you're interested in participating in a private preview of this feature, add your contact information to the [Dynamics 365 IOM Simulations interest form](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR7PfTHWf5-FKvJrqC3rlH_NUMENXVVdFWlNKWEtDR082NEFVVE5VRjVZTi4u).

Businesses using order management systems often struggle with visibility into the automated fulfillment decisions made by those systems, as well the predictability of outcomes over time. Running A/B testing on the outcomes of a fulfillment system or conducting experiments to discover better strategies must be performed on real-life orders and customers, risking impact on customer satisfaction, revenue, and costs.

The Intelligent Order Management AI simulations feature is a no-code, business user-friendly tool that allows you to run experiments on your data, not your customers. Intelligent Order Management AI simulations use your own data and repeatedly [sample that data](https://en.wikipedia.org/wiki/Monte_Carlo_method) based on parameters that you set for a given scenario. Such simulations can provide estimated results that can help you deploy new strategies with more confidence. Knowing the expected results of experiments such as swapping out fulfillment centers or adjusting the allowable distance for deliveries can help you make data-informed decisions that dramatically improve your business results.

> [!NOTE]
> All screenshots in this article are from a preproduction version of the simulation feature and may not accurately represent how the final product will appear.

## Access simulations

You can access simulations in the left navigation pane of Intelligent Order Management, just like you would access any other features. On the **Simulations** landing page, you'll see a list of all previous simulations you have run as shown in the following example image. 

![Simulations landing page showing list of all previous simulations](media/sims_landing.png)

You can open any previous simulation to see its settings and results. Also, you can compare the results of previous simulations side by side, as shown in the following example image.

![Previous simulations comparison](media/sims_compare.png)

## Create a simulation

To create a new simulation, at the top of the **Simulations** landing page, select **+New**. This opens a wizard that walks you through setting up your simulations step-by-step. The first screen contains several predefined scenario templates that you can start with, as shown in the following example image.

![Predefined simulations scenarios](media/sims_scenarios.png)

The predefined scenario templates work in the following ways.

- **Source optimization** - Want to see what would be the impact to your costs, delivery times, and inventory if you included or excluded different fulfillment sources within a service area? Source optimization simulations allow you to swap sources in and out and measure the impact to your fulfillment network. 
- **Demand shock impact** - What would the impact be on your current order management network if demand spiked by two or three times current levels in the next few months? How would those changes affect your restocking cadence? How much would it drive up your costs to maintain delivery times? Demand shock impact simulations enable you to simulate various order volumes in the future and see the resulting impacts on your distribution centers and overall network. 
- **Expand your fulfillment network** - Business expansion is a highly strategic and impactful decision that must be data-informed and future-proof. Expanding into a new geographic location, opening a new distribution center in a current service area, or tuning third-party logistics can have dramatic impacts on your inventory decisions, delivery times, and costs. Simulating the impact of business expansion across your order management network enables you to make decisions with more confidence.  
- **Introduce new products** - New product expansion can have cannibalization effects on your current product lines, and cause ripple effects across your order management network as buying patterns change. These changes can impact your carefully planned inventory operations, and your fulfillment and delivery plans. Simulating the impact of new product introduction gives you a future view of the expected impact of this type of expansion. 

> [!NOTE]
> For the initial version of the simulation feature, only the **source optimization** scenario will be available, with the other scenarios to follow in subsequent releases. 

Selecting the **Source optimization** scenario opens the **Create a simulation** wizard.

### Name your simulation

![Sims naming form](media/sim_name.png)

Name your simulation something you will recognize easily, such as "Max distance and source update for Los Angeles". The description field can be used as a "note", to add more details to help you remember the motivation or goals behind the simulation (or for others to understand the simulation at a glance). 

### Order types

![Sims order type step 1](media/sims_order_type1.png)

1. Indicator that displays the steps in the wizard, and how you're progressing
2. Setting panel where you configure the settings of the simulation. For this step, you're selecting from two order types: 
    1. Simulate future demand: choose a period of time in the future (ex: upcoming holiday season) and have Intelligent Order Management simulate what the demand will look like for that period
    2. Simulate a test order: create a test order or choose a previously created test order and simulate how Intelligent Order Management will fulfill that order
3. Map view of your order management network, which can be configured on the next step of the wizard 

For example, if you select "simulate future demand", two settings will be displayed:

![Sims future demand](media/sims_future_demand.png)

You can select a date range (ex: 11/15/22 to 12/31/22), and you can also select a "demand multiplier". If you think for example, your business has grown and you will do 2x the demand you had in previous years, you can set the multiplier to 2. Or if you're just curious how your network would handle 4x the demand, you can set the multiplier to 4, or any number you want.

### Fulfillment sources

On the next step, Intelligent Order Management will display the available fulfillment sources in both a list and map view, based on your settings from the previous step. On this screen, you can select or deselect any sources to include / exclude from the fulfillment plan.

![Sims source selection](media/sims_sources.png)

### Constraints

When you're done selecting sources, the next step will allow you to select constraints, such as location or source priority, maximum number of fulfillment sources, maximum distance between source to destination, and split order allowance. These are the same constraints available to the rest of Intelligent Order Management (look for "Business constraints" on [this help page](ifo.md)). 

![Sims constraints](media/sims_constraints.png)

### View results

Your Simulation is done! The results page will show business critical KPIs, and trends associated with the simulation you ran. You'll notice the numbers are presented with "lower and upper bounds". This is because the results are based on a single simulation, running repeatedly to produce a wide range of potential results. This "Monte Carlo method" will often provide an accurate approximation of an actual future result (expected result). The "main" number on the KPIs is the expected result, and the upper and lower bounds provide the min and max numbers from all the potential results. 

![Sims results](media/sims_results.png)

On the results page, you will find several areas.

1. Navigation back to your previous settings screens. You can go back to any previous setting and update it to iterate on the simulation you just ran. As an example, you experimented with 15 miles max distance, and want to use all the exact same settings to see what happens if you changed it to 20 miles. You can run this experiment without having to start over with a new simulation. Clicking on the "commit changes" button on the bottom of the screen will run the simulation again, and the results page will show deltas from the previous simulation.
2. Configuration summary will show all the settings for the current simulation.
3. Main KPI area will show all the business critical KPIs for your simulation.
4. Map / metrics view: will show on a map the fulfillment sources for this simulation. Toggling to metrics view will show you sources in a table format, which includes inventory counts, which source was selected to fulfill which products, distance, and more.

### Additional information

Intelligent Order Management simulations will reinvent the way to think about order management systems. No longer will you push orders through a system and just wait for results that show the impact on your customers. You can now simulate a wide variety of scenarios to bring some predictability to your fulfillments and can optimize the system yourself by uncovering efficiencies with experimentation. But much better than simple A/B testing, these experiments are performed on your data and results are simulated, without having impact on your real customers. Intelligent Order Management simulations puts the power of AI in your pocket so you can take ownership for improving your business.




