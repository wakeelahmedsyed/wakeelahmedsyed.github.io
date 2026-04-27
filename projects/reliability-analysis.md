<div style="font-family: 'Open Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif; color: #606c71; max-width: 100%; line-height: 1.5;">

  <div style="background-color: #159957; background-image: linear-gradient(120deg, #155799, #159957); padding: 2rem; border-radius: 6px; text-align: center; margin-bottom: 2rem;">
    <h1 style="color: #ffffff; margin: 0; font-size: 1.75rem; font-weight: normal; border-bottom: none;">Reliability & Availability Analysis</h1>
    <p style="color: rgba(255, 255, 255, 0.8); font-size: 1rem; margin-top: 0.5rem;">Attock Cement Pakistan Limited (ACPL) | Cement Mill Unit</p>
  </div>

  <div style="display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 2rem;">
    <div style="flex: 1; min-width: 150px; background: #eff1f3; padding: 15px; border-radius: 4px; text-align: center; border-bottom: 3px solid #159957;">
      <span style="display: block; font-size: 1.5rem; color: #155799; font-weight: bold;">79.36%</span>
      <span style="font-size: 0.7rem; text-transform: uppercase; letter-spacing: 1px;">Avg. Availability</span>
    </div>
    <div style="flex: 1; min-width: 150px; background: #eff1f3; padding: 15px; border-radius: 4px; text-align: center; border-bottom: 3px solid #159957;">
      <span style="display: block; font-size: 1.5rem; color: #155799; font-weight: bold;">4 Months</span>
      <span style="font-size: 0.7rem; text-transform: uppercase; letter-spacing: 1px;">Data Logging Period</span>
    </div>
    <div style="flex: 1; min-width: 150px; background: #eff1f3; padding: 15px; border-radius: 4px; text-align: center; border-bottom: 3px solid #159957;">
      <span style="display: block; font-size: 1.5rem; color: #155799; font-weight: bold;">Exponential</span>
      <span style="font-size: 0.7rem; text-transform: uppercase; letter-spacing: 1px;">Failure Distribution</span>
    </div>
  </div>

  <h2 style="color: #155799; font-weight: normal; border-bottom: 1px solid #eee; padding-bottom: 0.5rem; font-size: 1.5rem;">🚩 Executive Summary</h2>
  <p>
    The cement mill unit operates on a continuous or semi-continuous basis depending on market demand. Because shutdowns are dictated by stock levels and market fluctuations, preventative maintenance is rarely scheduled in advance. This analysis evaluated failure rate trends across multiple unit process modes over four months to determine steady-state availability and model the statistical reliability of the grinding process.
  </p>

  <blockquote style="border-left: 10px solid #eff1f3; margin: 1.5rem 10px; padding: 0.5rem 10px; color: #606c71; font-style: italic;">
    "By establishing that the overall failure rate remains constant over time, we successfully mapped unit breakdowns to predictable probability distributions—transitioning the plant from reactive assumptions to data-driven operational intelligence."
  </blockquote>

  <h2 style="color: #155799; font-weight: normal; border-bottom: 1px solid #eee; padding-bottom: 0.5rem; font-size: 1.5rem;">🛠️ Technical Approach</h2>
  
  <table style="width: 100%; border-collapse: collapse; margin: 1rem 0;">
    <tr>
      <td style="width: 30px; vertical-align: top; color: #159957; font-weight: bold; font-size: 1.2rem;">01</td>
      <td style="padding-bottom: 1.5rem;">
        <strong style="color: #222;">Failure Mode Logging & Categorization</strong><br>
        Collected comprehensive breakdown data from September 1 to December 31, 2019. Categorized all unscheduled and planned maintenance events to isolate specific operational bottlenecks.
      </td>
    </tr>
    <tr>
      <td style="width: 30px; vertical-align: top; color: #159957; font-weight: bold; font-size: 1.2rem;">02</td>
      <td style="padding-bottom: 1.5rem;">
        <strong style="color: #222;">Availability & Trend Analysis</strong><br>
        Calculated steady-state operational availability by evaluating moving failure rates, MTTR (Mean Time To Repair), and MTBMA (Mean Time Between Maintenance Actions).
      </td>
    </tr>
    <tr>
      <td style="width: 30px; vertical-align: top; color: #159957; font-weight: bold; font-size: 1.2rem;">03</td>
      <td style="padding-bottom: 1.5rem;">
        <strong style="color: #222;">Probability Distribution Modeling</strong><br>
        Applied Exponential distributions to model the overall unit reliability and Poisson distributions to analyze mutually exclusive, independent failure modes (e.g., ClkBinLL).
      </td>
    </tr>
  </table>

  <h2 style="color: #155799; font-weight: normal; border-bottom: 1px solid #eee; padding-bottom: 0.5rem; font-size: 1.5rem;">📊 Operational Availability Data</h2>

  <div style="border: 1.5px dashed #159957; background-color: #eff1f3; border-radius: 6px; padding: 2rem; text-align: center; margin-bottom: 1.5rem;">
    <span style="font-size: 2rem; display: block; margin-bottom: 0.5rem;">📉</span>
    <strong style="color: #155799; display: block; margin-bottom: 0.25rem;">[Visualization Placeholder: Moving Failure Rate Over Time]</strong>
    <p style="font-size: 0.85rem; margin: 0;">A line chart displaying a nearly straight, constant trend line across Sept, Oct, Nov, and Dec, proving the failure rate does not change significantly over time.</p>
  </div>
  
  <table style="width: 100%; border-collapse: collapse; font-size: 0.9rem;">
    <thead>
      <tr style="background-color: #159957; color: #ffffff;">
        <th style="padding: 10px; text-align: left; border-radius: 4px 0 0 0;">Month (2019)</th>
        <th style="padding: 10px; text-align: right;">MTBMA (hrs)</th>
        <th style="padding: 10px; text-align: right;">MTTR (hrs)</th>
        <th style="padding: 10px; text-align: right; border-radius: 0 4px 0 0;">Availability (%)</th>
      </tr>
    </thead>
    <tbody>
      <tr style="border-bottom: 1px solid #eee;">
        <td style="padding: 10px;">September</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">39.53</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">12.27</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">76.42%</td>
      </tr>
      <tr style="border-bottom: 1px solid #eee;">
        <td style="padding: 10px;">October</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">40.45</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">9.50</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">80.08%</td>
      </tr>
      <tr style="border-bottom: 1px solid #eee;">
        <td style="padding: 10px;">November</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">35.60</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">7.83</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">80.63%</td>
      </tr>
      <tr style="border-bottom: 1px solid #eee;">
        <td style="padding: 10px;">December</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">39.66</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">8.86</td>
        <td style="padding: 10px; text-align: right; font-family: monospace;">80.29%</td>
      </tr>
      <tr style="background-color: #eff1f3; font-weight: bold;">
        <td style="padding: 10px;" colspan="3">Average Operational Availability</td>
        <td style="padding: 10px; text-align: right; font-family: monospace; color: #155799;">79.36%</td>
      </tr>
    </tbody>
  </table>

  <h2 style="color: #155799; font-weight: normal; border-bottom: 1px solid #eee; padding-bottom: 0.5rem; font-size: 1.5rem; margin-top: 2.5rem;">📈 Reliability & Specific Failure Modes</h2>

  <p>Because the unit exhibits a constant failure rate, the overall reliability can be modeled as a continuous exponential distribution representing consecutive days of operation without breakdowns. Furthermore, isolated events like the <strong>ClkBinLL (Clinker Bin Low Level)</strong> failure follow a Poisson distribution.</p>

  <div style="display: flex; gap: 1rem; margin-top: 1.5rem; flex-wrap: wrap;">
    
    <div style="flex: 1; min-width: 250px;">
      <table style="width: 100%; border-collapse: collapse; font-size: 0.9rem;">
        <thead>
          <tr style="background-color: #159957; color: #ffffff;">
            <th style="padding: 10px; text-align: left; border-radius: 4px 0 0 0;">Consecutive Days w/o Breakdowns</th>
            <th style="padding: 10px; text-align: right; border-radius: 0 4px 0 0;">Reliability</th>
          </tr>
        </thead>
        <tbody>
          <tr style="border-bottom: 1px solid #eee;"><td style="padding: 10px;">1 Day</td><td style="padding: 10px; text-align: right; font-family: monospace; color: #159957; font-weight: bold;">54%</td></tr>
          <tr style="border-bottom: 1px solid #eee;"><td style="padding: 10px;">2 Days</td><td style="padding: 10px; text-align: right; font-family: monospace;">29%</td></tr>
          <tr style="border-bottom: 1px solid #eee;"><td style="padding: 10px;">3 Days</td><td style="padding: 10px; text-align: right; font-family: monospace;">16%</td></tr>
          <tr style="border-bottom: 1px solid #eee;"><td style="padding: 10px;">4 Days</td><td style="padding: 10px; text-align: right; font-family: monospace;">8%</td></tr>
          <tr style="border-bottom: 1px solid #eee;"><td style="padding: 10px;">5 Days</td><td style="padding: 10px; text-align: right; font-family: monospace;">5%</td></tr>
          <tr style="border-bottom: 1px solid #eee;"><td style="padding: 10px;">6 Days</td><td style="padding: 10px; text-align: right; font-family: monospace;">2%</td></tr>
        </tbody>
      </table>
    </div>

    <div style="flex: 1; min-width: 250px; display: flex; flex-direction: column; gap: 1rem;">
      <div style="border: 1.5px dashed #159957; background-color: #eff1f3; border-radius: 6px; padding: 1.5rem; text-align: center; flex: 1;">
        <strong style="color: #155799; display: block; margin-bottom: 0.25rem;">[Viz: Reliability Curve]</strong>
        <p style="font-size: 0.8rem; margin: 0;">Exponential decay curve showing reliability dropping from 54% (Day 1) to 2% (Day 6).</p>
      </div>
      <div style="border: 1.5px dashed #159957; background-color: #eff1f3; border-radius: 6px; padding: 1.5rem; text-align: center; flex: 1;">
        <strong style="color: #155799; display: block; margin-bottom: 0.25rem;">[Viz: Poisson Prob. ClkBinLL]</strong>
        <p style="font-size: 0.8rem; margin: 0;">Bar chart indicating maximum probability of exactly 1 failure for the ClkBinLL process at 29%.</p>
      </div>
    </div>
  </div>

  <h2 style="color: #155799; font-weight: normal; border-bottom: 1px solid #eee; padding-bottom: 0.5rem; font-size: 1.5rem; margin-top: 2.5rem;">💡 Impact & Future Scope</h2>
  <ul style="padding-left: 1.5rem;">
    <li style="margin-bottom: 0.5rem;"><strong>Statistical Mapping:</strong> Proved that overall plant failures are not entirely random but follow predictable exponential distributions, allowing for better predictive maintenance framing.</li>
    <li style="margin-bottom: 0.5rem;"><strong>Granular Isolation:</strong> Successfully isolated independent events (ClkBinLL) to assign a Poisson distribution, establishing a framework for addressing specific root causes one at a time.</li>
    <li><strong>Automation Roadmap:</strong> Initiated the development of a dynamic dashboard utilizing Excel Power Query and Microsoft Power BI to fully automate future failure data logging and reliability analysis.</li>
  </ul>

  <div style="text-align: center; margin-top: 3rem;">
    <a href="../" style="display: inline-block; padding: 0.5rem 1rem; color: #155799; border: 1px solid #155799; border-radius: 4px; text-decoration: none; font-size: 0.9rem;">← Back to Portfolio</a>
  </div>

</div>
