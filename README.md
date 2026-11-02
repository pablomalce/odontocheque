# OdontoCheque

A small Ruby on Rails prototype where registered dentists in Argentina sign in, pick an oral-care brand and product, and download a printable product voucher ("cheque") as a PDF.

## Context

Built by Pablo Malczewski between December 2020 and February 2021 (9 commits), starting from the [Le Wagon Rails Devise template](https://github.com/lewagon/rails-templates). The UI is in Spanish. The brand and product images (Sensodyne, Parodontax, Corega) are used as sample catalog content; the repository does not record whether this was commissioned work, so treat it as a personal prototype.

## What it does

- Sign-up and login with Devise. Besides email and password, a user registers with a username, first and last name, province (a fixed list of Argentine provinces) and a 6-digit professional registration number ("matrícula"). A custom validation stops two users from sharing the same registration number within the same jurisdiction (CABA vs. the rest of the country).
- After login, the profile page shows the user's details and the brand logos; a brand page lists its products.
- "Emitir cheque" renders a PDF with WickedPDF/wkhtmltopdf: a voucher background image with the dentist's name, registration number, province and the current date printed on top.

Not finished: the voucher number on the PDF is a hard-coded placeholder, the PDF does not yet depend on the chosen product, and no code path creates rows in the `cheques` table (number, user, product); the seed file tries to, without a user or product, and fails at that step. The test files are Rails scaffolds with no real tests.

## Stack

Ruby 2.6.6, Rails 6.0, PostgreSQL, Devise, Simple Form, Bootstrap 4, Webpacker, WickedPDF + wkhtmltopdf-binary.

## Running it locally

Needs Ruby 2.6.6, PostgreSQL and Yarn.

```bash
bundle install
yarn install
rails db:create db:migrate db:seed   # brands and products seed; the final cheque step currently errors
rails server
```

## Status

Unfinished prototype from early 2021. Archived, not maintained.
