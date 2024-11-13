Burden Load Testing Action
==========================

![GitHub release (latest by date)](https://img.shields.io/github/v/release/burden-load/action) ![GitHub license](https://img.shields.io/github/license/burden-load/action)

A GitHub Action for performing customizable load testing using the Burden CLI tool, written in Go. This Action is designed for developers and DevOps engineers who want to integrate performance testing into their CI/CD pipelines.

Features
--------

*   Supports multiple HTTP methods (GET, POST, PUT, DELETE, etc.).
*   Allows specification of various load testing parameters.
*   Outputs key metrics (Throughput, Response Time, Latency).
*   Configurable detailed reporting for comprehensive performance analysis.

Usage
-----

### Basic Setup

Add the following to your workflow file (e.g., `.github/workflows/load-test.yml`):

    name: Load Test
    
    on:
      push:
        branches:
          - main
    
    jobs:
      load-test:
        runs-on: ubuntu-latest
        steps:
          - name: Checkout code
            uses: actions/checkout@v2
    
          - name: Run Load Testing Action
            uses: burden-load/action@v1
            with:
              url: 'https://example.com/api'
              method: 'GET'
              users: 10
              requests: 100
    

### Inputs

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Required</th>
      <th>Default</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>url</code></td>
      <td>The target URL for the load test.</td>
      <td>Yes</td>
      <td>N/A</td>
    </tr>
    <tr>
      <td><code>method</code></td>
      <td>HTTP method for requests (e.g., GET, POST).</td>
      <td>No</td>
      <td>GET</td>
    </tr>
    <tr>
      <td><code>users</code></td>
      <td>Number of concurrent users for the test.</td>
      <td>No</td>
      <td>1</td>
    </tr>
    <tr>
      <td><code>requests</code></td>
      <td>Total number of requests to perform.</td>
      <td>No</td>
      <td>100</td>
    </tr>
    <tr>
      <td><code>duration</code></td>
      <td>Test duration in seconds (alternative to <code>requests</code>).</td>
      <td>No</td>
      <td>N/A</td>
    </tr>
    <tr>
      <td><code>detailed_report</code></td>
      <td>Set to <code>true</code> for a full report.</td>
      <td>No</td>
      <td>false</td>
    </tr>
  </tbody>
</table>

### Example with Detailed Reporting

    - name: Run Load Testing with Detailed Report
      uses: burden-load/action@v1
      with:
        url: 'https://example.com/api'
        method: 'POST'
        users: 20
        duration: 60
        detailed_report: true
    

### Outputs

After the test, the Action will output basic metrics to the workflow logs. If `detailed_report` is enabled, the Action will provide additional metrics, such as error rates and peak load.

License
-------

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.