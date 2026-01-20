---
title: "Anticipating things I didn’t think about"
description: "What MCP taught me about balancing automation power with usability for network compliance tooling."
pubDate: 2026-01-20
---

I’ve been working on a tool to automate network compliance. As the project matured, I hit a hurdle. I wanted to build a drive-thru menu of user-friendly actions (read: GET endpoints) so I didn’t have to crack open the core script every time someone had a new idea. I’m one person, and there are so many people who have ideas beyond my own. That sounded like unnecessary work.

## Power vs. usability

If a tool is powerful but intimidating, people fall back to their spreadsheets because spreadsheets are familiar. My goal was to make this tool feel like a souped-up spreadsheet, not a coding exercise. But as I dug deeper, I realized a bigger question needed answering: **Is traditional, static automation even the right way to do this?**

## Enter MCP

The more I tried to “hard-code” a friendly interface, the more I realized I was just building another rigid system. I spent the last few months learning about Model Context Protocol (MCP) from John Capobianco (<https://www.linkedin.com/in/john-capobianco-644a1515/>).

In traditional automation, the inputs and outputs are tightly defined. Checking if a device name matches a regex pattern is easy. The difficulty arises when you want to expose the logic of the audit so the team can cover new checks you haven’t even thought of yet.

Instead of building tightly defined functions, MCP lets us give an LLM the **building blocks** it needs to do the work for us:

* **Tools**: Simple, generic actions like `get_sites()` or `get_devices()`.
* **Resources**: Dynamic data sources that enrich the model. This could be a cache of UUIDs to optimize speed, or a translation layer that helps the model understand that a “Wireless Access Point,” an “AP,” and a “WAP” are all the same thing.
* **Prompts**: The steering wheel. They connect the tools and resources while influecning the model to make certain decisions. Prompts provide guidelines like “only use GET endpoints” or “consult specific resources before planning the audit.”

## This is the way (for now)

Technically, I’m still “hard-coding” tools, resources, and prompts. When I look at the investment of time versus the rigidity of what I could have created with a legacy automation approach, I’m still in the positive in terms of time spent and value gained. I may be building functionality that I haven’t even accounted for yet.

Where I’m unclear—likely because of lack of experience—is the deterministic outcomes of a traditional script versus the variability you might get when prompting a model. This is likely a prompt issue at best; at worst, it’s something outside of our control.
