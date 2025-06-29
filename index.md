---
layout: page
title: Overview
permalink: /
---

<div class="prose mx-auto py-8">

  <h1>Retention Radar: Customer Churn Data Prep</h1>

  <img src="{{ site.baseurl }}/assets/images/cancellation_rate.png"
       alt="Cancellation Rate"
       class="w-full rounded-lg shadow-md my-6">

  <div class="bg-blue-50 border-l-4 border-blue-300 p-4 mb-8">
    <h2>Key Insights</h2>
    <ul>
      <li>Customers who received a discount exhibit a significantly higher cancellation rate than those who didn’t.</li>
      <li>This suggests discount-driven sign-ups may lack long-term commitment, pointing to a need for targeted retention strategies.</li>
    </ul>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-12">
    <div class="bg-white border border-gray-200 rounded-lg shadow p-6">
      <h2>Context</h2>
      <p>An online streaming service has experienced a worrying uptick in customer cancellations over the past quarter. Leadership suspects hidden patterns in subscription behavior and listening habits are driving churn—and they want a data-driven diagnosis before building any prediction models.</p>
    </div>
    <div class="bg-white border border-gray-200 rounded-lg shadow p-6">
      <h2>Scope</h2>
      <p>Identify customers at high risk of canceling their subscription based on their streaming activity and account status over the past three months.</p>
    </div>
  </div>

  <hr class="border-gray-200 my-12">

  <section class="bg-white border border-gray-200 rounded-lg shadow p-6 mb-8">
    <h2>Objective</h2>
    <ol>
      <li>Scope the churn-analysis project end to end</li>
      <li>Ingest customer and listening-history data into Python</li>
      <li>Clean and standardize all fields, resolve data issues, and derive new columns</li>
      <li>Explore and visualize key churn drivers both independently and after joining tables</li>
      <li>Deliver a final, non-null, numeric DataFrame with engineered features ready for modeling</li>
    </ol>
  </section>

  <section class="bg-white border border-gray-200 rounded-lg shadow p-6 mb-8">
    <h2>Process</h2>
    <ol>
      <li>Project scoping &amp; stakeholder alignment
        <ul>
          <li>Confirmed churn definition: any customer with non-null Cancellation Date</li>
          <li>Data sources: customers.csv, listening_history.xlsx (two sheets)</li>
          <li>Deliverables: cleaned DataFrame + EDA visuals</li>
        </ul>
      </li>
      <li>Data ingestion
        <ul>
          <li>Loaded customer profiles and streaming-history CSVs using Pandas</li>
          <li>Verified schema, identified missing or invalid entries, then imputed or filled missing values (e.g. defaulted blank plans to ‘Basic (Ads)’, converted ‘Discount?’ flags)</li>
        </ul>
      </li>
      <li>Data cleaning &amp; feature derivation
        <ul>
          <li>Harmonized date fields (subscription start, cancellation) to datetime</li>
          <li>Imputed or removed missing values in key columns (subscription rate , subscription plan)</li>
          <li>Engineered new features: Number of Sessions, %Pop, %Podcasts, Email cleanup (stripped prefix), Genre normalization ('Pop Music' → 'Pop'), Audio ID split into type & numeric ID</li>
        </ul>
      </li>
      <li>Exploratory analysis
        <ul>
          <li>Discount vs. churn
            <ul>
              <li>Only 7 customers received a discount, and around 86% of them canceled—compared to about 30% churn among non-discount users.</li>
            </ul>
          </li>
          <li>Distribution of Listening Sessions
            <div class="my-4">
              <img src="{{ site.baseurl }}/assets/images/listening_sessions_distribution.png"
                   alt="Distribution of Listening Sessions per Customer"
                   class="w-full rounded-md shadow-sm">
            </div>
            <p>We counted how many separate listening sessions each user had over three months. Most people fell between 1–5 sessions, suggesting a sizable low-engagement group.</p>
          </li>
          <li>Genre Popularity
            <table class="w-full table-auto border-collapse my-4">
              <thead>
                <tr class="bg-gray-100">
                  <th class="border px-4 py-2 text-left">Genre</th>
                  <th class="border px-4 py-2 text-right">Count</th>
                </tr>
              </thead>
              <tbody>
                <tr><td class="border px-4 py-2">Pop</td><td class="border px-4 py-2 text-right">267</td></tr>
                <tr><td class="border px-4 py-2">Hip Hop</td><td class="border px-4 py-2 text-right">88</td></tr>
                <tr><td class="border px-4 py-2">Country</td><td class="border px-4 py-2 text-right">68</td></tr>
                <tr><td class="border px-4 py-2">Jazz</td><td class="border px-4 py-2 text-right">48</td></tr>
                <tr><td class="border px-4 py-2">Comedy</td><td class="border px-4 py-2 text-right">19</td></tr>
                <tr><td class="border px-4 py-2">True Crime</td><td class="border px-4 py-2 text-right">15</td></tr>
              </tbody>
            </table>
            <p>Pop dominates with more than three times the listens of the next genre. Understanding whether fans of particular genres churn at different rates could uncover new retention levers.</p>
          </li>
        </ul>
      </li>
      <li>Final DataFrame prep
        <ul>
          <li>Isolated numeric predictors with no nulls</li>
          <li>Produced a feature-correlation heatmap against churn</li>
          <li>Merged all numeric predictors (session counts, percent-listens, cancel flag) into a clean modeling DataFrame—ready for scaling and risk-segmentation downstream</li>
        </ul>
        <div class="my-6">
            <img src="{{ site.baseurl }}/assets/images/feature_correlation_heatmap.png"
                 alt="Feature Correlation Heatmap"
                 class="w-full rounded-md shadow-sm">
        </div>
        <p class="font-semibold">Key correlations:</p>
        <ul class="list-disc list-inside ml-6">
          <li><em>Percent Pop vs. Cancelled:</em> 0.586 – higher Pop listen share is strongly linked with churn</li>
          <li><em>Discount? vs. Cancelled:</em> 0.472 – discounted customers are more likely to cancel</li>
          <li><em>Number of Sessions vs. Cancelled:</em> –0.334 – more sessions correlate with lower churn</li>
        </ul>
      </li>
    </ol>
  </section>

  <section class="bg-white border border-gray-200 rounded-lg shadow p-6 mb-8">
    <h2>Output</h2>
    <ul>
      <li>A clean, feature-rich Pandas DataFrame primed for machine learning</li>
      <li>A Jupyter notebook showcasing EDA visualizations  </li>
    </ul>
  </section>

  <section class="bg-white border border-gray-200 rounded-lg shadow p-6">
    <h2>Design Principles</h2>
    <ul>
      <li>Alignment &amp; Proximity: Grouped related metrics (engagement vs. tenure) for intuitive comparison</li>
      <li>Enclosure: Used distinct chart backgrounds to separate analyses before and after table join</li>
      <li>Colour &amp; Hue: Applied a diverging palette to highlight positive vs. negative churn correlations</li>
    </ul>
  </section>

</div>