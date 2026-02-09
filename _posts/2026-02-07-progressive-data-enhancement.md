---
layout: post
title: Progressive Data Enhancement
date: 2026-02-07 14:53 +0000
---

[Progressive enhancement](https://en.wikipedia.org/wiki/Progressive_enhancement) is a web development design strategy where you build a fully working version of the content, before adding any styles or interactivity for those who can use them. This has been a cornerstone of the "GDS approach" to front end web design and development when building public digital services. It's [how GOV.UK was built](https://technology.blog.gov.uk/2016/09/19/why-we-use-progressive-enhancement-to-build-gov-uk/), and it's a requirement of the [Service Manual](https://www.gov.uk/service-manual/technology/using-progressive-enhancement) today. Building services this way is how to ensure that they are the most resilient and accessible for all, which is why [BBC services](https://www.bbc.co.uk/accessibility/forproducts/guides/html/progressive-enhancement/) and [Wikipedia](https://en.wikipedia.org/wiki/Progressive_enhancement) are also built this way.

In my work on [Digital Screening](https://www.digital-prevention-services.nhs.uk/screening/) at NHS England, I've been thinking that there are lessons from this approach that could be applied to how we think about data in the NHS. I'll call this "Progressive *Data* Enhancement".

## Design assuming no data first

In traditional Progressive Enhancement, you create the content in HTML first, then add the styling in CSS, then add any interactive behaviour in Javascript.

In Progressive Data Enhancement, you design a working service on the assumption that there is data, but you don't have access to it. Let’s say you’re building a service that lets someone book in for an x-ray. You don't know the patient's name, age, gender. You don't know if they've visited your service before, and what their outcomes were. You don't know what diseases they have, what medication they're on etc.

If you can build this service, then you can move onto adding the data sources in to make this service better. You could access your own service's data to see if the patient has visited you before. You could use the [NHS Personal Demographics Service](https://digital.nhs.uk/services/personal-demographics-service) to retrieve their demographic data so it doesn't need to be typed in again. You could access national data to see if they've had another x-ray in the last 6 months. You could access their NHS Login to get their saved preferences so you can send them app notifications instead of letters like they like. You could access the [National Disease Registration Service](https://digital.nhs.uk/ndrs) to see if the patient has a relevant disease. You could access their GP records to see if they have already reported symptoms relevant to your service. You could put all of this into an AI model to recommend next steps.

But, like styling (CSS) and interactive behaviours (Javscript) in traditional Progressive Enhancement, you don't get to play with these toys until the content structure (HTML) works on its own. You build a usable service without the data, and then add the data on top. All of these make the service better, but none of them are allowed to make it exist.

This sounds slow and frustrating, so why should you do this?

### Reason 1: You'll build something useful quicker

Data needs to be collected before it can be used, and your service might be the first to be collecting it. But even if that's not the case, it might be in a system you don't have access to yet. You might be waiting for a Data Protection Impact Assessment (DPIA) to be completed. The supplier of that may have given you a schema to tide you over, but often it turns out the production data doesn't match the schema in reality.

This means that "the data" becomes an untested assumption, and in agile software development, you want to be removing untested assumptions as soon as possible. By ensuring your service works without this data, you have removed that assumption.

### Reason 2: It will reduce bugs

I have heard of complete, clean and semantic data stores in the public sector, but I have yet to see one with my own eyes. More often you will find data that is out of date, or stored in free text fields, or PDFs, or distributed across regions. If your service can work without having access to this data, it becomes a lot easier to handle the instances when it is wrong.

### Reason 3: It ensures more inclusive services

The same data often changes in different contexts. While a user might have told one service a fact about themselves, they may have a different answer for that same question on your service. This may seem surprising, but there are many instances where a fact about yourself changes on the context. For example, while a student may maintain their GP correspondence to their childhood home, they may prefer to put their student accommodation address for an unexpected visit to the hospital. We come across this sort of thing a lot: names, genders, privacy settings, communication preferences can all change depending on the context and for reasons we should and must support. If your service can work without relying on external data, it can better support these cases too.

### Reason 4: It improves resilience

There are also lots of ways that a data source can go wrong. A server might go down. A legal basis might change. A user may [retract consent](https://digital.nhs.uk/services/national-data-opt-out). A foreign government bans its export. If you have built your service first to survive without the data source, it can keep operating. The best analogy for this kind of "graceful degradation" is that your service is more like an escalator than a lift: if it breaks, then you can still use it as stairs.

## Designing services out of data standards is tempting but risky

There is a growing frustration about the state of data in the NHS: It is fragmented, inconsistent, hard to access, and often unfit for secondary use. Faced with this, there's a temptation to force the fix at source by designing the data standards first, and then insisting that services are built to produce and consume that data in a prescribed way. You can see this instinct in approaches that start with canonical data models, or in attempts to standardise user interactions through things like FHIR questionnaires.

Progressive Data Enhancement offers a different path. Instead of forcing services to conform to data standards up front, it allows the data to fall out of user needs, rather than forcing users into data standards.