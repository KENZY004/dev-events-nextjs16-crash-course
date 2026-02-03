# PostHog post-wizard report

The wizard has completed a deep integration of your Next.js App Router project. PostHog analytics has been configured with client-side event tracking using the modern `instrumentation-client.ts` approach, which is the recommended method for Next.js 15.3+. A reverse proxy has been set up through Next.js rewrites to improve tracking reliability by reducing ad-blocker interference.

## Integration Summary

The following changes were made to your project:

1. **Installed `posthog-js`** - The PostHog JavaScript SDK for client-side analytics
2. **Configured `next.config.ts`** - Added rewrites for PostHog reverse proxy (`/ingest` routes)
3. **Updated `instrumentation-client.ts`** - PostHog initialization with error tracking enabled
4. **Added event tracking** - Custom events in key user interaction points

## Events Implemented

| Event Name | Description | File |
|------------|-------------|------|
| `explore_events_clicked` | User clicked the 'Explore Events' button to scroll to the events section | `components/ExploreBtn.tsx` |
| `event_card_clicked` | User clicked on an event card to view event details | `components/EventCard.tsx` |
| `navbar_link_clicked` | User clicked a navigation link in the navbar (Home, Events, Create Event) | `components/Navbar.tsx` |

## Event Properties

### explore_events_clicked
- `button_location`: Location of the button (e.g., "hero_section")

### event_card_clicked
- `event_title`: Title of the event
- `event_slug`: URL slug of the event
- `event_location`: Location of the event
- `event_date`: Date of the event
- `event_time`: Time of the event

### navbar_link_clicked
- `link_name`: Name of the clicked link (e.g., "Home", "Events", "Create Event", "Logo")

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behavior, based on the events we just instrumented:

### Dashboard
- [Analytics basics](https://us.posthog.com/project/298153/dashboard/1150595) - Main analytics dashboard with all insights

### Insights
- [Event Card Clicks](https://us.posthog.com/project/298153/insights/8xKwbrTh) - Tracks how often users click on event cards
- [Explore Events Button Clicks](https://us.posthog.com/project/298153/insights/Qd0DUnfG) - Tracks explore button engagement
- [Navigation Clicks](https://us.posthog.com/project/298153/insights/vtJA4qm4) - Tracks navbar link engagement
- [Explore to Event Card Funnel](https://us.posthog.com/project/298153/insights/2pfp6tVk) - Conversion funnel from exploration to event selection
- [Overall User Engagement](https://us.posthog.com/project/298153/insights/Tu8StqOa) - Combined view of all tracked interactions

## Environment Variables

The following environment variables have been configured in `.env`:

```
NEXT_PUBLIC_POSTHOG_KEY=phc_d8RGCdk1b1gjmkqrUSFdoFpdfZS8TSy4beKjTOszVlR
NEXT_PUBLIC_POSTHOG_HOST=https://us.i.posthog.com
```

### Agent skill

We've left an agent skill folder in your project at `.claude/skills/nextjs-app-router/`. You can use this context for further agent development when using Claude Code. This will help ensure the model provides the most up-to-date approaches for integrating PostHog.
