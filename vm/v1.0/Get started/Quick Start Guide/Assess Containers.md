---
title: "Assess Containers"
excerpt: ""
---
# What are containers?

Containers are specialized groupings of resources needed to run a software application.  Unlike traditional virtual machines, containers simply borrow the operating system and computing resources from their host.  Using container images as blueprints, containers only consist of whatever tools are necessary for running their assigned application.

This lightweight design is what makes containers fast, effective, and widely used in modern networks.

# What makes containers risky?

Container environment architecture has inherent security concerns.  Although containers are designed to be isolated, any attacker that gains access to a container could theoretically find a way to the host machine.  Hosts can have thousands of containers running concurrently, so the security of the images from which they are built is extremely important.

To this end, InsightVM offers container image assessment along with several other features to ensure that your containers are as low-risk as possible.

# Examine your container images

With your Insight Agent up and running, let’s take a look at what container images have been found in your network.  Open the **Containers** tab in your menu to see a list of images that the Insight Agent has found so far.  By default, your most vulnerable images will be listed first.  See [Managing Container Images](doc:managing-container-images) for more information about this screen.

# Assess your images

InsightVM will automatically assess images as long as it has access to them.  In cases when images are not accessible, you can assess them manually.  See [Assessing an image](doc:managing-container-images#section-assessing-an-image) for instructions on how to do this.

# Connect a repository

InsightVM supports connections to [several container registries](doc:working-with-containers#section-supported-registries).  Connect to any of these registries to access repositories of container images that you can use in your environment.  See [Managing Container Connections](doc:managing-container-connections) to learn how.
[block:callout]
{
  "type": "success",
  "title": "Milestone complete!",
  "body": "Outstanding!  You should now have visibility on any container images in your environment and any vulnerabilities they have.  You should also have a repository connection set up for one of the supported registries.\n\nReady to buy?  See our [Next Steps](doc:next-steps) page."
}
[/block]