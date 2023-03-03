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

Businesses that use order management systems often struggle to gain visibility into the automated fulfillment decisions that those systems make, and also with the predictability of outcomes over time. Real-life orders must be used to run A/B testing on the outcomes of a fulfillment system, or to conduct experiments to discover better strategies. Therefore, there's a risk that customer satisfaction, revenue, and costs might be affected.

The AI simulations feature in Intelligent Order Management is a no-code, business user–friendly tool that lets you run experiments on your data, not your customers. Intelligent Order Management AI simulations use your own data and [repeatedly sample it](https://en.wikipedia.org/wiki/Monte_Carlo_method), based on parameters that you set for a given scenario. The estimated results that these simulations provide can help you more confidently deploy new strategies. When you know the expected results of experiments such as swapping out fulfillment centers or adjusting the allowable distance for deliveries, you can make data-informed decisions that can help dramatically improve your business results.

> [!NOTE]
> All screenshots in this article are from a preproduction version of the AI simulations feature. They might not accurately represent how the final product will appear.

## Access simulations

You can access simulations, like other features, in the left navigation pane of Intelligent Order Management. The **Simulations** list page shows a list of all previous simulations that you've run, as shown in the following example.

![List of all previous simulations on the Simulations list page.](media/sims_landing.png)

You can open any previous simulation to view its settings and results. You can also compare the results of previous simulations side by side, as shown in the following example.

![Side-by-side comparison of previous simulations.](media/sims_compare.png)

## Create a simulation

To create a new simulation, select **New** at the top of the **Simulations** list page to open the **Create a simulation** wizard. This wizard guides you step by step through the process of setting up a new simulation.

The first preliminary page of the wizard shows several predefined scenario templates that you can start with, as shown in the following example.

![Predefined simulation scenarios in the wizard.](media/sims_scenarios.png)

The predefined scenario templates work in the following ways:

- **Source optimization** – What will be the impact on your costs, delivery times, and inventory if you include or exclude different fulfillment sources in a service area? Source optimization simulations let you swap sources in and out, and measure the impact on your fulfillment network.
- **Demand shock impact** – What will be the impact on your current order management network if demand spikes by two or three times the current levels in the next few months? How will those changes affect your restocking cadence? How much will it drive up your costs to maintain delivery times? Demand shock impact simulations let you simulate different order volumes in the future and view the resulting impact on your distribution centers and overall network.
- **Expand your fulfillment network** – Business expansion is a highly strategic and impactful decision that must be data-informed and future-proof. Expanding into a new geographic location, opening a new distribution center in a current service area, or tuning third-party logistics can have a dramatic impact on your inventory decisions, delivery times, and costs. By simulating the impact of business expansion across your order management network, you can more confidently make decisions.
- **Introduce new products** – New product expansion can have cannibalization effects on your current product lines, and can cause ripple effects across your order management network as buying patterns change. These changes can affect your carefully planned inventory operations, and your fulfillment and delivery plans. By simulating the impact of new product introduction, you can get a future view of the expected impact of this type of expansion.

> [!NOTE]
> For the initial version of the AI simulations feature, only the **Source optimization** scenario is available. Other scenarios will be added in later releases.

When you select a scenario, the second preliminary page of the wizard appears, where you enter a name and description for the simulation.

### Name your simulation

Name your simulation something that you'll easily recognize, such as **Max distance and source update for Los Angeles**. In the **Simulation description** field, you can add note-type details to help you remember the motivation or goals behind the simulation (or to help other users understand the simulation at a glance).

![Simulation name and description entered in the wizard.](media/sim_name.png)

When you've finished entering information on this page, select **Next** to open the page for the first step of the main part of the wizard.

### Specify an order type

In the first step of the wizard, you specify the type of orders that you want to simulate.

![Page for step 1 of the wizard, where an order type is specified.](media/sims_order_type1.png)

Here's an explanation of the elements on the page. (The numbers correspond to the numbered callouts in the preceding illustration.)

1. An indicator that shows the steps in the wizard and your progress through them.
1. A settings pane where you configure the settings for the simulation. For the first step, you select between two types of orders:

    - **Simulate future demand** – Select this option to have Intelligent Order Management simulate what the demand will look like for a future period (for example, an upcoming holiday season).
    - **Simulate a test order(s)** – Select this option to simulate how Intelligent Order Management will fulfill a new test order that you create or an existing test order that you select.

    Depending on the option that you select, additional settings become available. For example, if you select the **Simulate future demand** option, you can specify a date range (such as November 15, 2022, through December 31, 2022). You can also select a "demand multiplier." Therefore, if you think that your business has grown, and that you'll have two times the demand that you had in previous years, you can set the **Demand multiplier** field to **2**. Or, if you're just curious how your network would handle four times the demand, you can set the **Demand multiplier** field to **4**.

    ![Additional settings for the Simulate future demand order type.](media/sims_future_demand.png)

1. A map view of your order management network. You can configure this view in the next step of the wizard.

When you've finished entering information on this page, select **Next** to open the page for the next step of the wizard.

### Select fulfillment sources

In the next step of the wizard, Intelligent Order Management shows the available fulfillment sources in both a list view and a map view, depending on your settings from the previous step. On this page, you can select or clear the selection of any source to specify the sources that are included in the fulfillment plan.

![Page for step 2 of the wizard, where fulfillment sources are selected.](media/sims_sources.png)

When you've finished selecting sources on this page, select **Next** to open the page for the next step of the wizard.

### Select constraints

In the next step, you can select constraints, such as the location or source priority, the maximum number of fulfillment sources, the maximum distance between source to destination, and the split order allowance. These constraints are the same constraints that are available to the rest of Intelligent Order Management. For more information, see [Business constraints](ifo.md#business-constraints).

![Page for step 3 of the wizard, where constraints are selected.](media/sims_constraints.png)

When you've finished selecting constraints on this page, select **Confirm** to view the results of the simulation.

### View results

The results page shows business-critical key performance indicators (KPIs) and trends that are associated with the simulation that you ran. Notice that upper and lower bounds are presented for each KPI. The reason is that the results are based on a single simulation that's run repeatedly to produce a wide range of potential results. This so-called [Monte Carlo method](https://en.wikipedia.org/wiki/Monte_Carlo_method) often provides an accurate approximation of an actual future result (expected result). The main number for each KPI is the expected result, and the upper and lower bounds represent the minimum and maximum numbers from all the potential results.

![Example of simulation results.](media/sims_results.png)

Here's an explanation of the different areas on the results page. (The numbers correspond to the numbered callouts in the preceding illustration.)

1. Navigation to the pages for previous steps of the wizard. You can go back to any previous step and update the settings to iterate the simulation that you just ran.

    For example, you've experimented with a maximum distance of 15 miles. You now want to see what happens if the maximum distance is changed to 20 miles but all the other settings remain the same. You can run this experiment without having to start a completely new simulation.

    When you select **Commit changes** at the bottom of the page, the simulation will be run again, and the results page will show deltas from the previous simulation.

1. The configuration summary, which shows all the settings for the current simulation.
1. The main KPI area, which shows all the business-critical KPIs for the current simulation.
1. **Map** and **Metrics** views that you can switch between. The **Map** view that shows a map of the fulfillment sources for the current simulation. The **Metrics** view shows the sources in a table format that identifies which source was selected to fulfill which products, and that includes inventory counts, distance, and more.

## Additional information

Intelligent Order Management AI simulations will change the way that you think about order management systems. You no longer have to push orders through a system and wait for results that show the impact on your customers. You can now simulate a wide range of scenarios to bring some predictability to your fulfillment, and you can optimize the system yourself by uncovering efficiencies through experimentation. These experiments are much better than simple A/B testing, because they're performed on your data, and the results are simulated. Therefore, there's no impact on your real customers. Intelligent Order Management AI simulations put the power of AI in your hands, so that you can take ownership over improving your business.
