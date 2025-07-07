<h1>🚗 Dynamic Parking Pricing with Real-Time Visualization</h1>

<p>
A real-time dynamic pricing system for urban parking spaces, built entirely with <b>Python, Pandas, Numpy, Pathway, Bokeh, and Panel</b>. 
The project uses streaming data from multiple parking lots to compute smart, adaptive prices based on real-time occupancy, demand, traffic, and seasonality.
</p>

<hr>

<h2>📊 <u>Project Overview</u></h2>

<ul>
    <li>Real-time pricing for 14 urban parking spaces over 73 days of data.</li>
    <li>Data sampled every 30 minutes between 8:00 AM and 4:30 PM.</li>
    <li>Dynamic price adjustment based on occupancy, queue length, traffic, special events, vehicle type, and day-of-week seasonality.</li>
    <li>Visualizations for each parking lot and vehicle category using <b>Bokeh</b>.</li>
</ul>

<hr>

<h2>🛠 <u>Technology Stack</u></h2>

<ul>
    <li>Python 3</li>
    <li>Pandas & Numpy (data processing)</li>
    <li>Pathway (streaming data simulation and windowing)</li>
    <li>Bokeh (interactive plots)</li>
    <li>Panel (dashboard layout)</li>
</ul>

<hr>

<h2>📦 <u>Project Architecture</u></h2>

<p>The system simulates real-time parking data, applies different pricing models, and streams visual dashboards:</p>

<pre>
┌─────────────┐   Stream CSV per Lot   ┌─────────────┐   Compute Prices   ┌──────────────┐
│  Parking    │  ───────────────────▶  │ Pathway     │  ───────────────▶  │ Bokeh Plots  │
│  Lot Data   │                        │ Streaming   │                   │ + Panel UI   │
└─────────────┘                        └─────────────┘                   └──────────────┘
</pre>

<hr>

<h2>📐 <u>Pricing Models Implemented</u></h2>

<h3>Model 1: Baseline Linear Pricing</h3>
<ul>
    <li>Price increases linearly with occupancy levels.</li>
    <li>Formula: <code>Price = 10 + α * (MaxOccupancy - MinOccupancy) / Capacity</code></li>
</ul>

<h3>Model 2: Demand-Based Pricing with Seasonality</h3>
<ul>
    <li>Demand function includes occupancy, queue length, traffic, special events, vehicle type.</li>
    <li>Smoothed seasonality introduced using a sine wave based on weekday.</li>
    <li>Vehicle-specific price multipliers applied for cars, bikes, trucks, etc.</li>
    <li>Final Formula:</li>
</ul>

<pre>
NormalizedDemand = α·(Occupancy/Capacity) + β·QueueLength - γ·Traffic + δ·SpecialDay

SeasonalityBoost = 0.1 * sin( (Weekday/6) * 2π )

BasePrice = 10 * (1 + λ * NormalizedDemand)

FinalPrice = BasePrice * VehicleWeight * (1 + SeasonalityBoost)
</pre>

<hr>

<h2>📈 <u>Visualization Features</u></h2>

<ul>
    <li>Interactive, real-time line plots of price evolution per parking lot.</li>
    <li>Separate plots for each vehicle type (car, bike, truck, etc.).</li>
    <li>Comparison with baseline pricing for transparency.</li>
</ul>

<hr>

<h2>📁 <u>Project Structure</u></h2>

<ul>
    <li><code>parking_stream_&lt;lot&gt;.csv</code>: Simulated stream data for each lot.</li>
    <li><code>dynamic_pricing.py</code>: Main streaming, pricing, and visualization code.</li>
    <li><code>README.html</code>: This project documentation.</li>
</ul>

<hr>

<h2>💡 <u>Potential Future Extensions</u></h2>

<ul>
    <li>Incorporate competitor pricing for price optimization.</li>
    <li>Vehicle rerouting suggestions when lots reach full capacity.</li>
    <li>More complex seasonal patterns (e.g., monthly, event-based).</li>
</ul>

<hr>

<h2>📝 <u>Contact</u></h2>

<p>For questions or collaboration, please reach out via GitHub issues or email.</p>
