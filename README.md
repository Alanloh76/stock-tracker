# Stock Tracker

A single-page stock tracker for a three-outlet café chain (Jurong, Orchard, Tampines), backed by Supabase.

## Features

- A tab per outlet, with category filters and a "Low only" toggle
- Per-item −/+ controls for stock on hand and reorder level, saved to Supabase with a Save button
- Items at or below their reorder level are marked **Low**
- An "Order from suppliers" tab that totals the shortfall across all outlets, with a Copy button
- Sign in with a username (or email), sign out, and change your own password
- Admins get a Users page to add people with an initial password, reset passwords, change roles, and activate, deactivate or remove accounts

## Usage

Open `stock-tracker.html` in a browser and sign in with a Supabase account that has an active profile in the project. The data lives in the `public.stock_counts` table, which is protected by row-level security, so only signed-in members can read or change it.

## Accounts

Logins use Supabase Auth (`auth.users`); each login has a row in `public.profiles` with its username, role (`admin` or `member`), active flag and a must-change-password flag. People added with just a username sign in as `<username>@tracker.test` behind the scenes, so they only ever type the username. Anyone given an initial password is asked to choose their own the first time they sign in.

Account changes go through the `admin-users` Supabase Edge Function, which checks the caller is an active admin and holds the service key, so it never reaches the browser.
