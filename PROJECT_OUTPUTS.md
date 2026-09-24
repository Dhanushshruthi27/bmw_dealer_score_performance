# BMW Dealer Scoreboard Performance - Project Outputs

This document records deployed AWS outputs and screenshot evidence for the BMW Dealer Scoreboard Performance project.

> **Sharing note:** Redact AWS account IDs, account aliases, regions, bucket names, URLs, and other deployment-specific identifiers before sharing screenshots publicly.

## AWS project outputs

Screenshots are stored in `project_outputs/images/` and referenced using the corresponding output tag.

### `s3_bucket_name` - Amazon S3 data bucket

**Output tag:** `s3_bucket_name`

**Tagline:** The Amazon S3 data bucket is organized with separate dataset folders for customer feedback, dealers, sales, and service data.

**Observed contents:**

- `customer_feedback/`
- `dealer/`
- `sales/`
- `service/`

**Purpose:** Stores the source CSV datasets used by AWS Glue and Amazon Athena for dealer performance scoring.

**Screenshot:**

Save the provided screenshot as:

```text
project_outputs/images/s3_bucket_name.png
```

![Amazon S3 data bucket containing dealer scorecard datasets](project_outputs/images/s3_bucket_name.png)

### `athena_score_view` - Amazon Athena scoring view

**Output tag:** `athena_score_view`

**Tagline:** The dealer scoring query completed successfully in Amazon Athena and the score view is available for analysis.

**Observed contents:**

- Database: `bmw_dealer_score_performace_db`
- Tables: `customer_feedback`, `dealer`, `sales`, and `service`
- View: `dealer_score_vw`
- Query status: `Completed`

**Purpose:** Confirms that the source tables are cataloged and the dealer performance scoring view can be queried successfully.

**Screenshot:**

Save the provided screenshot as:

```text
project_outputs/images/athena_score_view.png
```

![Amazon Athena dealer scoring view query completed successfully](project_outputs/images/athena_score_view.png)

### `quicksight_analysis` - Amazon QuickSight dealer performance analysis

**Output tag:** `quicksight_analysis`

**Tagline:** The QuickSight analysis presents dealer performance scores, revenue, ranking, and service activity in an interactive table.

**Observed contents:**

- Data source: `dealer_score_vw`
- Grouped by: `dealer_id`, `dealer_name`, and `region`
- Metrics: `dealer_performance_score`, `revenue`, `dealer_rank`, and `service_count`
- Visual type: Table

**Purpose:** Provides a visual comparison of dealer performance across regions using the Athena scoring view.

**Screenshot:**

Save the provided screenshot as:

```text
project_outputs/images/quicksight_analysis.png
```

![Amazon QuickSight dealer performance analysis](project_outputs/images/quicksight_analysis.png)

### `quicksight_top_dealer_filter` - QuickSight top-dealer filter

**Output tag:** `quicksight_top_dealer_filter`

**Tagline:** A QuickSight filter for dealer rank `1` identifies the highest-ranked dealer and displays the corresponding score and revenue.

**Observed contents:**

- Filter condition: `dealer_rank` equals `1`
- Dealer ID: `D007`
- Dealer: BMW Los Angeles Pacific
- Region: North America
- Performance score: `70`
- Revenue: `3,186,500`

**Purpose:** Demonstrates that the QuickSight analysis can filter the scoring view to isolate the top-ranked dealer.

**Screenshot:**

Save the provided screenshot as:

```text
project_outputs/images/quicksight_top_dealer_filter.png
```

![Amazon QuickSight top-ranked dealer filter](project_outputs/images/quicksight_top_dealer_filter.png)

### `quicksight_ranked_analysis` - QuickSight ranked dealer analysis

**Output tag:** `quicksight_ranked_analysis`

**Tagline:** The QuickSight table ranks all dealers in ascending order and compares performance score, revenue, rank, and service activity.

**Observed contents:**

- Data source: `dealer_score_vw`
- Visual type: Table
- Sort order: `dealer_rank`, ascending
- Grouped by: `dealer_id`, `dealer_name`, and `region`
- Measures: `dealer_performance_score`, `revenue`, `dealer_rank`, and `service_count`
- Ranked results: positions `1` through `10`

**Purpose:** Provides an ordered view of dealer performance for comparison across regions and business metrics.

**Screenshot:**

Save the provided screenshot as:

```text
project_outputs/images/quicksight_ranked_analysis.png
```

![Amazon QuickSight ranked dealer analysis](project_outputs/images/quicksight_ranked_analysis.png)

### `quicksight_kpi_score_count` - QuickSight performance score KPI

**Output tag:** `quicksight_kpi_score_count`

**Tagline:** A QuickSight KPI visual summarizes the distinct dealer performance scores and displays a result of `10`.

**Observed contents:**

- Visual type: Key Performance Indicator (KPI)
- Field: `dealer_performance_score`
- Aggregation: `Count distinct`
- Displayed value: `10`

**Purpose:** Provides a compact KPI summary of the distinct performance score values available in the dealer scoring view.

**Screenshot:**

Save the provided screenshot as:

```text
project_outputs/images/quicksight_kpi_score_count.png
```

![Amazon QuickSight performance score KPI](project_outputs/images/quicksight_kpi_score_count.png)

### `quicksight_score_by_region_chart` - QuickSight regional score chart

**Output tag:** `quicksight_score_by_region_chart`

**Tagline:** A QuickSight horizontal bar chart compares dealer performance scores by dealer ID and uses region colors to reveal geographic differences.

**Observed contents:**

- Visual type: Horizontal bar chart
- Y-axis: `dealer_id`
- Value: `dealer_performance_score`
- Group/color: `region`
- Regions shown: Asia Pacific, Europe, Middle East, and North America

**Purpose:** Visualizes dealer performance score differences across regions and makes the ranking pattern easier to compare.

**Screenshot:**

Save the provided screenshot as:

```text
project_outputs/images/quicksight_score_by_region_chart.png
```

![Amazon QuickSight regional dealer performance score chart](project_outputs/images/quicksight_score_by_region_chart.png)

## Output reference

The Terraform output definitions are maintained in `terraform/outputs.tf`. Keep the output tag names in this document aligned with that file when infrastructure outputs change.
