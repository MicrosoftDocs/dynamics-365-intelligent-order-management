---
author: derekkwanpm
description: This topic provides an overview for the AI Simulations feature for IOM.
ms.date: 09/23/2022
ms.topic: conceptual
ms.author: derekkwan

title: IOM Simulations (Coming soon)
---


# IOM Simulations (Coming soon)

[!include [banner](includes/banner.md)]

*Please note this feature is currently in development with a planned Private Preview in 2023. If you are interested in previewing this feature, please drop your email address here.*

Businesses using an order management system often struggle with visibility into automated fulfillment decisions happening behind the scenes, as well as maintaining some predictability of outcomes over time. Additionally, testing the outcomes of a fulfillment system, or attempting to run experiements to discover better strategies to deploy, have to be performed on real-life orders and customers, risking negative impact on revenue and customer sastisfaction.

The new Simulations feature for IOM is a no-code, business user friendly tool that allows you to run experiments on your data, not your customers. IOM Simulations uses your own data and repeatedly [samples that data](https://en.wikipedia.org/wiki/Monte_Carlo_method) over and over again based on parameters that you set for a given scenario, and provides estimated results from those scenarios to help you deploy new strategies with more confidence. Knowing the expected values of swapping out fulfillment centers or adjusting the allowable distance for deliveries, among other experiments, will help you make data-informed decisions that can dramatially improve your business results.

Please note all screenshots below are from a pre-production version of the feature, and may not demonstrate how the end product may appear.

## Accessing IOM Simulations

You will be able access Simulations in the left menu of the IOM application, just like you would access any other features of IOM. On the Simulations landing page will be a list of all previous simulations you have run. You can open any previous simulation to see settings and results.

![Sims landing page](/topics/media/sims_landing.png)

You can also compare the results of previous simulations side by side:

![Sims results comparison](/topics/media/sims_compare.png)

## Creating a simulation

From the Simulations landing page, you can create a new simulation from the top menu. This will lead you to a wizard that will walk you step-by-step through setting up your simulations. The first screen will contain several pre-defined scenario templates that you can start with:

![Simulations scenarios](/topics/media/sims_scenarios.png)

1. Source optimization: want to see what would be the impact to your costs, delivery times, and inventory if you included or excluded different fulfillment sources within a service area? Source optimiation simulations allow you to swap sources in and out and measure what would happen to your fulfillment network. 
2. Demand shock impact: 
3. Expand your fulfillment network:
4. Introduce new products

For the first version of Simulations, we will have available the source optimization scenario, with the others to follow in upcoming releases. Clicking on the "source optimization" scenario will start the setup wizard:

### Naming your simulation

![Sims naming form](/topics/media/sim_name.png)

### Order types

![Sims order type step 1](/topics/media/sims_order_type1.png)

1. Indicator that displays the steps in the wizard, and how you're progressing
2. Setting panel where you conifgure the settings of the simulation. For this step, you are selecting from two order types: 
    1. Simulate future demand: choose a period of time in the future (ex: upcoming holiday season) and have IOM simulate what the demand will look like for that period
    2. Simulate a test order: create a test order or choose a previously created test order and simulate how IOM will fulfill that order
3. Map view of your order management network, which can be configured on the next step of the wizard 

For example, if you select "simulate future demand", two settings will be displayed:

![Sims future demand](/topics/media/sims_future_demand.png)

You can select a date range (ex: 11/15/22 to 12/31/22), and you can also select a "demand multiplier". If you think for example, your business has grown and you will do 2x the demand you had in previous years, you can set the multiplier to 2. Or if you're just curious how your network would handle 4x the demand, you can set the multiplier to 4, or any number you want.

### Fulfillment sources

On the next step, IOM will display the available fulfillment sources in both a list and map view, based on your settings from the previous step. On this screen, you can select or deselect any sources to include / exclude from the fulfillment plan.

![Sims source selection](/topics/media/sims_sources.png)

### Constraints

When you're done selecting sources, the next step will allow you to select constraints, such as location or source priority, maximum number of fulfillment sources, maximum distance between source to destination, and split order allowance. These are the same constraints available to the rest of IOM (look for "Business constraints" on [this help page](https://learn.microsoft.com/dynamics365/intelligent-order-management/ifo)). 

![Sims constraints](/topics/media/sims_constraints.png)

## Viewing results

![Sims results](/topics/media/sims_results.png)



