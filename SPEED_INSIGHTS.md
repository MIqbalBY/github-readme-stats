# Vercel Speed Insights Integration

This project is configured to use Vercel Speed Insights to monitor real-world performance metrics and Core Web Vitals.

## Overview

GitHub Readme Stats has Speed Insights enabled to track real user performance data for the API endpoints and any web interfaces. This helps monitor:
- Real User Monitoring (RUM) metrics
- Core Web Vitals (LCP, FID, CLS)
- API response times
- Performance scores across different regions
- User experience metrics

## What is Speed Insights?

Vercel Speed Insights provides real-time performance monitoring by measuring actual user experiences on your deployed application. Unlike synthetic testing, Speed Insights captures metrics from real visitors, giving you accurate insights into how your application performs in production.

## Configuration

Speed Insights is enabled through two components:

### 1. vercel.json Configuration

The `vercel.json` file includes the Speed Insights configuration:

```json
{
  "speedInsights": {
    "enable": true
  }
}
```

This enables Vercel's Speed Insights, which automatically tracks:
- Core Web Vitals (LCP, FID, CLS, TTFB, FCP, INP)
- Performance scores
- Regional performance data
- Browser and device metrics

### 2. Package Dependency

The `@vercel/speed-insights` package is included in the project dependencies:

```json
{
  "dependencies": {
    "@vercel/speed-insights": "^1.1.0"
  }
}
```

While this project primarily serves API endpoints that generate SVG images, the package is available for future use if any HTML interfaces or landing pages are added.

## Core Web Vitals Tracked

Speed Insights measures the following Core Web Vitals:

- **LCP (Largest Contentful Paint)**: Measures loading performance. Good LCP occurs within 2.5 seconds.
- **FID (First Input Delay)**: Measures interactivity. Good FID occurs within 100 milliseconds.
- **CLS (Cumulative Layout Shift)**: Measures visual stability. Good CLS is less than 0.1.
- **TTFB (Time to First Byte)**: Measures server response time.
- **FCP (First Contentful Paint)**: Measures when the first content is rendered.
- **INP (Interaction to Next Paint)**: Measures responsiveness to user interactions.

## Viewing Speed Insights Data

To view the Speed Insights data:

1. Go to your [Vercel Dashboard](https://vercel.com/dashboard)
2. Select the GitHub Readme Stats project
3. Click on the **Speed Insights** tab
4. View real-time performance metrics including:
   - Core Web Vitals scores
   - Performance over time
   - Geographic performance distribution
   - Device and browser breakdown
   - Individual page/endpoint performance

## For API-First Applications

Since GitHub Readme Stats is primarily an API service that generates SVG cards, Speed Insights will focus on:

- **TTFB (Time to First Byte)**: Critical for API response times
- Server-side performance metrics
- Geographic latency measurements
- API endpoint performance comparison

If you add any HTML pages or web interfaces in the future, Speed Insights will automatically start tracking full Core Web Vitals for those pages.

## Implementation for Future HTML Interfaces

If you add HTML pages or a web interface to this project, you can implement Speed Insights tracking using one of these methods:

### Option 1: Using the Script Tag (Recommended for HTML)

Add this to your HTML files before the closing `</body>` tag:

```html
<script>
  window.si = window.si || function () { (window.siq = window.siq || []).push(arguments); };
</script>
<script defer src="/_vercel/speed-insights/script.js"></script>
```

### Option 2: Using the Package (For React/Next.js/Other Frameworks)

If you add a React-based interface:

```javascript
import { injectSpeedInsights } from '@vercel/speed-insights';

injectSpeedInsights();
```

For Next.js (Pages Router):

```jsx
import { SpeedInsights } from '@vercel/speed-insights/next';

function MyApp({ Component, pageProps }) {
  return (
    <>
      <Component {...pageProps} />
      <SpeedInsights />
    </>
  );
}
```

For Next.js (App Router):

```jsx
import { SpeedInsights } from '@vercel/speed-insights/next';

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>
        {children}
        <SpeedInsights />
      </body>
    </html>
  );
}
```

## Privacy and Compliance

Vercel Speed Insights is designed with privacy in mind:
- No personal identifiable information (PII) is collected
- No cookies are used for tracking
- Compliant with GDPR, CCPA, and other privacy regulations
- Data is aggregated and anonymized
- IP addresses are not stored

Learn more about [Vercel Speed Insights Privacy Policy](https://vercel.com/docs/speed-insights/privacy-policy).

## For Self-Hosted Instances

If you're self-hosting this project on Vercel:

1. Fork the repository
2. Deploy to your Vercel account
3. Enable Speed Insights in your project settings (if not already enabled via vercel.json)
4. Speed Insights will automatically start collecting data once enabled
5. Access your Speed Insights dashboard through your Vercel project

> **Note:** Enabling Speed Insights adds new routes scoped at `/_vercel/speed-insights/*` after your next deployment.

## Limits and Pricing

Speed Insights follows Vercel's usage-based pricing:

- **Hobby Plan**: 2,500 data points per month included
- **Pro Plan**: 10,000 data points per month included
- **Enterprise Plan**: Custom limits

A "data point" is recorded each time a Core Web Vitals metric is collected from a user visit.

For more information, see [Speed Insights Limits and Pricing](https://vercel.com/docs/speed-insights/limits-and-pricing).

## Troubleshooting

If Speed Insights data is not appearing:

1. **Check Deployment**: Ensure Speed Insights was enabled before or during the deployment
2. **Wait for Data**: Initial data may take 24-48 hours to populate with meaningful insights
3. **Verify Configuration**: Check that `vercel.json` contains the `speedInsights` configuration
4. **Check Routes**: Verify that `/_vercel/speed-insights/script.js` is accessible
5. **Review Limits**: Ensure you haven't exceeded your plan's data point limits

### Verifying Speed Insights is Active

After deployment, you can verify Speed Insights is active by:

1. Checking for the `/_vercel/speed-insights/script.js` route in your deployment
2. Looking for Speed Insights script tags in any HTML pages
3. Viewing the Speed Insights tab in your Vercel dashboard

## Additional Resources

- [Vercel Speed Insights Documentation](https://vercel.com/docs/speed-insights)
- [Speed Insights Package Documentation](https://vercel.com/docs/speed-insights/package)
- [Understanding Core Web Vitals](https://web.dev/vitals/)
- [Speed Insights API Reference](https://vercel.com/docs/speed-insights/api-reference)

## Integration with Analytics

Speed Insights works seamlessly with Vercel Web Analytics (already enabled in this project). Together they provide:

- **Web Analytics**: Traffic patterns, page views, visitor counts
- **Speed Insights**: Performance metrics, Core Web Vitals, user experience data

Both features complement each other to give you a complete picture of your application's performance and usage. See [ANALYTICS.md](./ANALYTICS.md) for more information about Web Analytics configuration.
