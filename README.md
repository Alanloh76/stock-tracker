# Stock Tracker

A single-page stock tracker for a three-outlet café chain (Jurong, Orchard, Tampines), backed by Supabase.

## Features

- A tab per outlet, with category filters and a "Low only" toggle
- Per-item −/+ controls for stock on hand and reorder level, saved to Supabase with a Save button
- Items at or below their reorder level are marked **Low**
- An "Order from suppliers" tab that totals the shortfall across all outlets, with a Copy button

## Usage

Open `stock-tracker.html` in a browser and sign in with a Supabase account that has an active profile in the project. The data lives in the `public.stock_counts` table, which is protected by row-level security, so only signed-in members can read or change it.
