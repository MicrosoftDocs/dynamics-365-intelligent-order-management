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

Please note this feature is currently in development with a planned Private Preview in 2023. If you are interested in previewing this feature, please drop your email address here.

Businesses using an order management system often struggle with visibility into automated fulfillment decisions happening behind the scenes, as well as maintaining some predictability of outcomes over time. Additionally, testing the outcomes of a fulfillment system, or attempting to run experiements to discover better strategies to deploy, have to be performed on real-life orders and customers, risking negative impact on revenue and customer sastisfaction.

The new Simulations feature for IOM is a no-code, business user friendly tool that allows you to run experiments on your data, not your customers. IOM Simulations uses your own data and repeatedly [samples that data](https://en.wikipedia.org/wiki/Monte_Carlo_method) over and over again based on parameters that you set for a given scenario, and provides estimated results from those scenarios to help you deploy new strategies with more confidence. Knowing the expected values of swapping out fulfillment centers or adjusting the allowable distance for deliveries, among other experiments, will help you make data-informed decisions that can dramatially improve your business results.

Please note all screenshots below are from a pre-production version of the feature, and may not demonstrate how the end product may appear.

You will be able access Simulations in the left menu of the IOM application, just like you would access any other features of IOM. On the Simulations landing page will be a list of all previous simulations you have run. You can open any previous simulation to see settings and results.

![Sims landing page](/topics/media/sims_landing.png)

You can also compare the results of previous simulations side by side:

![Sims results comparison](/topics/media/sims_compare.png)


## Creating alerts

From the Simulations landing page, you can create a new simulation from the top menu. This will lead you to a wizard that will walk you step-by-step through setting up your simulations. The first screen will contain several pre-defined scenario templates that you can start with:

![Simulations scenarios](/topics/media/sims_scenarios.png)

1. Source optimization: want to see what would be the impact to your costs, delivery times, and inventory if you included or excluded different fulfillment sources within a service area? Source optimiation simulations allow you to swap sources in and out and measure what would happen to your fulfillment network. 
2. Demand shock impact: 
3. Expand your fulfillment network:
4. Introduce new products

For the first version of Simulations, we will have available the source optimization scenario, with the others to follow in upcoming releases.



