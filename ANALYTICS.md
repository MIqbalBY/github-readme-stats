# Vercel Web Analytics Integration

This project is configured to use Vercel Web Analytics to track usage and performance metrics.

## Overview

GitHub Readme Stats is deployed on Vercel as a serverless API that generates dynamic SVG cards. Web Analytics has been enabled to monitor:
- API endpoint usage
- Performance metrics
- Traffic patterns
- Geographic distribution of requests

## Configuration

Web Analytics is enabled through two components:

### 1. vercel.json Configuration

The `vercel.json` file includes the analytics configuration:

```json
{
  "analytics": {
    "enable": true
  }
}
```

This enables Vercel's built-in Web Analytics, which automatically tracks:
- Page views and API requests
- Performance metrics (Web Vitals)
- Traffic sources
- Geographic data

### 2. Package Dependency

The `@vercel/analytics` package is included in the project dependencies for potential future use with any HTML-based interfaces or landing pages.

```json
{
  "dependencies": {
    "@vercel/analytics": "^1.4.1"
  }
}
```

## Viewing Analytics Data

To view the analytics data:

1. Go to your [Vercel Dashboard](https://vercel.com/dashboard)
2. Select the GitHub Readme Stats project
3. Click on the **Analytics** tab
4. View metrics including:
   - Request volume over time
   - Response times
   - Status codes
   - Geographic distribution
   - Top requested endpoints

## Privacy and Compliance

Vercel Web Analytics is privacy-focused and compliant with data protection regulations:
- No cookies are used
- No personal data is collected
- No cross-site tracking
- Compliant with GDPR, CCPA, and other privacy regulations

Learn more about [Vercel Analytics Privacy Policy](https://vercel.com/docs/analytics/privacy-policy).

## Custom Events (Optional)

While this project primarily serves SVG images via API endpoints, custom events can be tracked if HTML pages are added in the future:

```javascript
import { track } from '@vercel/analytics';

// Track custom events
track('card_generated', {
  type: 'stats',
  username: 'example'
});
```

## For Self-Hosted Instances

If you're self-hosting this project on Vercel:

1. Fork the repository
2. Deploy to your Vercel account
3. Analytics will be automatically enabled based on the `vercel.json` configuration
4. Access your analytics through your Vercel dashboard

No additional configuration is needed - Web Analytics will start tracking as soon as your deployment receives traffic.

## Troubleshooting

If analytics data is not appearing:

1. Ensure you're viewing the correct project in the Vercel dashboard
2. Wait 24-48 hours for initial data to populate
3. Verify the deployment was successful
4. Check that `vercel.json` contains the analytics configuration

For more information, visit the [Vercel Web Analytics Documentation](https://vercel.com/docs/analytics).

## Integration with Speed Insights

This project also has **Vercel Speed Insights** enabled, which complements Web Analytics by providing real-time performance monitoring and Core Web Vitals tracking. While Web Analytics focuses on traffic and usage patterns, Speed Insights focuses on performance metrics and user experience.

Together, these tools provide a complete picture of your application's health:
- **Web Analytics**: Traffic, page views, visitor counts, geographic distribution
- **Speed Insights**: Performance metrics, Core Web Vitals, response times, user experience

For more information about Speed Insights configuration and usage, see [SPEED_INSIGHTS.md](./SPEED_INSIGHTS.md).
