---
categories: []
tags: ["docs"]
title: "Introduction"
linkTitle: "Introduction"
date: 2022-06-20
description:
weight: 1
---

<div class="alert alert-warning">
    <i class="fa fa-warning"></i>
Vulnman is in a really early stage of development. Feel free to use, test it and please report bugs and other ideas.
You should <b>not</b> use it in production, because there may be breaking changes in the database schema.
</div>

<h2>What is Vulnman?</h2>
<a id = "what-is-vulnman"></a>

<div class="row">
  <div class="col-lg-12 col-md-12">
    <p>
      Vulnman is a free and open-source pentest management and collaboration software.
      Manage your pentest projects and their related assets using the Vulnman web interface.
      Vulnman comes with a simple to use report generator.
      This allows the pentesters to focus on finding vulnerabilities.
    </p>
    <p>
      It is built using the powerful <a href="https://www.djangoproject.com/" rel="noopener noreferrer">Django Framework</a>.
    </p>
  </div>
</div>


<h2 class="more-bottom">Features</h2>

<div class="row">
  <div class="col-lg-4 col-md-4 col-xs-12">
    <h3>Unlimited Users and Projects</h3>
    <p>
      Despite other solutions, vulnman does not limit the amount of users or projects.
    </p>
  </div>
  <div class="col-lg-4 col-md-4 col-xs-12">
    <h3>Report Generator</h3>
    <p>
      Vulnman contains a simple to use pentest report generator.
    Never waste your time struggling with Word documents.
    </p>
  </div>
  <div class="col-lg-4 col-md-4 col-xs-12">
    <h3>Customizable</h3>
    <p>
      Vulnman can be customized at multiple places. Some of them are:
      <a href="/docs/advanced-topics/custom-report-templates/">Report Template</a>,
      <a href="/docs/advanced-topics/vulnerability-templates/">Vulnerability Templates</a>,
      <a href="/docs/advanced-topics/checklists/">Checklists</a>
    </p>
  </div>
</div>

<hr>

<div class="row">
  <div class="col-lg-4 col-md-4 col-xs-12">
    <h3>Markdown Syntax</h3>
    <p>
      Vulnman allows you to write your texts in markdown (mostly).
    </p>
  </div>
  <div class="col-lg-4 col-md-4 col-xs-12">
    <h3>Vulnerability Management</h3>
    <p>
      Vulnman includes simple features to manage vulnerabilities of your projects.
      This includes <a href="/docs/advanced-topics/vulnerability-templates/">Vulnerability Templates</a>
      and CVSS scoring.
    </p>
  </div>
  <div class="col-lg-4 col-md-4 col-xs-12">
    <h3>Checklists and To Dos</h3>
    <p>
      Track your tasks during the pentest.
      Did you already check for SQL-Injection?
      Never miss a check anymore!
    </p>
  </div>
</div>

<hr>

<div class="row">
  <div class="col-lg-4 col-md-4 col-xs-12">
    <h3>Responsible Disclosure</h3>
    <p>
      Vulnman integrates features to support bug hunters during the responsible disclosure process.
        Share vulnerabilities discovered in third party software to their vendor, export advisories and more.
    </p>
  </div>
  <div class="col-lg-4 col-md-4 col-xs-12">
    <h3>Multi Language Support</h3>
    <p>
      By default, vulnmans report and vulnerabilities are tracked in english.
      However, you can easily configure it to use your language.
    </p>
  </div>
  <div class="col-lg-4 col-md-4 col-xs-12">
    <h3>REST-API</h3>
    <p>
      The REST-API is work in progress!
    </p>
  </div>
</div>



<h2>More information</h2>

<p>
  This page is just a brief introduction to what Vulnman is all about, and many
  technical details have been omitted here for the sake of presentation.
  <ul>
    <li>
      If you're a current or potential Vulnman user, you may want to check out the
      <a href="/docs/">documentation</a>.
    </li>
    <li>
      If you're a developer, there's dedicated
      <a href="/docs/#developer-documentation">developer documentation</a>.
    </li>
    <li>
      Need help, or just want to join the conversation? Learn more about
      <a href="/community/">help, support, and the community</a>.
    </li>
  </ul>
</p>
