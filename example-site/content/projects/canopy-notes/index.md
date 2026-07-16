---
title: "Canopy Notes"
draft: false
weight: 30
summary: "A field notebook for urban tree surveys that keeps observations tidy, searchable, and easy to publish."
subtitle: "A publishable field notebook for urban tree surveys."
heroImage: "hero.svg"
heroAlt: "Notebook preview for Canopy Notes showing tree observations and a small map panel."
---

## Problem

Volunteer survey notes were easy to collect but hard to review. Photos, species names, coordinates, and follow-up tasks drifted apart after each walk.

## Approach

Canopy Notes stores each observation as a page bundle with front matter for species, condition, and location. A small build step emits a GeoJSON index for mapping while the site remains readable without JavaScript.

## Result

Survey teams can now publish a public record and keep a maintainable private archive from the same source files.
