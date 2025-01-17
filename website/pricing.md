---
title: Pricing
layout: page
---

<link rel="stylesheet" href="/assets/css/subpage.css">

<div class="grid grid-cols-1 gap-2 lg:grid-cols-3 mb-12">
  {% include /pricing/core.html  %}
  {% include /pricing/satellites.html  %}
  {% include /pricing/ci.html  %}
</div>

<div class="text-3xl font-semibold mt-10"> FAQ</div>

<h2 class="text-2xl font-semibold mb-5 mt-20" id="what-is-an-active-user">What is an active user?<span class="hide"><a href="#what-is-an-active-user">¶</a></span></h2>

An active user is a user that has triggered a Satellite build at least three times during a month. Triggering a build can be done by either performing a Satellite build directly via the earthly CLI, or indirectly, by pushing code to a repository, and that push being picked up by a CI that uses a Earthly Satellites to perform the build.

<h2 class="text-2xl font-semibold mb-5 mt-20" id="zero-margin-compute">What is zero-margin compute?<span class="hide"><a href="#zero-margin-compute">¶</a></span></h2>

Zero-margin compute is a pricing model where the cost of compute is passed on directly to the user, without any profit-generating margin. This allows us, the CI vendor, to better align our incentives with the end-user. Slow builds should not mean more profit for us.

<h2 class="text-2xl font-semibold mb-5 mt-10" id="compute">How much does compute cost?<span class="hide"><a href="#compute">¶</a></span></h2>

The cost of compute is based on the AWS rack price for the instances that are used underneath, plus the cost of cache storage and the cost of network ingress/egress incurred. All of these costs are packaged as an all-inclusive per-minute cost and is then passed on directly to the user, without any profit-generating margin.

<div class="grid grid-cols-4">
<div class="font-semibold text-xl border-b flex">Instance type</div>
<div class="font-semibold text-xl border-b flex">Specs </div>
<div class="font-semibold text-xl border-b flex">Price per minute</div>
<div class="font-semibold text-xl border-b flex">Included minutes cost multiplier</div>
</div>

<div class="grid grid-cols-4 border-b">
<div class="py-4"><span class="font-semibold">small</span></div>
<div class="py-4">1 CPUs, 4 GB RAM, 22 GB cache</div>
<div class="py-4">Coming soon</div>
<div class="py-4">0.5X</div>
</div>

<div class="grid grid-cols-4 border-b">
<div class="py-4"><span class="font-semibold">medium</span></div>
<div class="py-4">2 CPUs, 8 GB RAM, 45 GB cache</div>
<div class="py-4">Coming soon</div>
<div class="py-4">1X</div>
</div>

<div class="grid grid-cols-4">
<div class="py-4"><span class="font-semibold">large</span></div>
<div class="py-4">4 CPUs, 16 GB RAM, 90 GB cache</div>
<div class="py-4">$0.0100</div>
<div class="py-4">2X</div>
</div>

<h2 class="text-2xl font-semibold mb-5 mt-20" id="usage-tracked">How is my usage of Satellites tracked?<span class="hide"><a href="#usage-tracked">¶</a></span></h2>

The usage of Satellites is tracked by monitoring the Satellites for active builds. If there are no active builds,the Satellite goes to sleep automatically after some time. When a Satellite is asleep, it is not billed for compute. When a build is started, the Satellite is woken up automatically and billed for compute.

<h2 class="text-2xl font-semibold mb-5 mt-20" id="how-many-satellites">How many Satellites do I need?<span class="hide"><a href="#how-many-satellites">¶</a></span></h2>

The number of Satellites depends on the amount of workload they need to handle. For maximum performance, you can create a different Satellite for each CI pipeline. In some setups, where the CI pipelines are small, that might be an overkill. The best method to determine the number of satellites is to start with one or two, and add more as needed.

Earthly prints information on build startup about how loaded the Satellite is currently. This can be used as a guide to determine if more Satellites are needed.

<h2 class="text-2xl font-semibold mb-5 mt-20" id="how-are-active-users-tracked">How are active users tracked?<span class="hide"><a href="#how-are-active-users-tracked">¶</a></span></h2>

The number of active users is tracked by monitoring who triggered the build. The build may be triggered either directly by the user in their terminal, or indirectly by a CI system. In the latter case, the triggering user is inferred via commit metadata. Each user needs to trigger the build at least three times during a month to be counted as an active user.

At the end of a billing cycle, if the number of paid users is greater than the number of active users, the difference is refunded to the user in the form of statement credit.
