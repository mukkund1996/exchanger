# Exchanger
### A simple low-dependency forex exchange estimator
This is a hobby web server created exclusively in rust from the ground up. It has zero-to-minimal dependencies. The cargo crate contains 2 binaries and are the following:
## Webserver Binary
- Multi-threaded webserver listening to requests on a pre-defined port. 
- Queries for the latest forex rates and returns the estimate of the rates in a given duration in the future. 

## Cronjob Binary
- Repeatedly runs the querying and estimation process on a pre-defined interval of time.
- If the rate exceeds the prescribed threshold, then the program proceeds to send an email through an external API. 

# Setup
## Environment Variables
The application depends on the following environment variables:
```bash
# Threshold value of the rate; when exceeded the email is sent
RATE_THRESHOLD
# The interval of the cronjob
EMAILER_INTERVAL
# The recipent of the email notification
USER_EMAIL
# Verified source email address - need to be configured in SendGrid 
SOURCE_EMAIL
# API key from SendGrid
SENDGRID_API_KEY
# Maximum number of threads in the ThreadPool. May vary with your machine.
MAX_WORKERS
```
## Development Build
To create a development build of the binaries, run the following:
### Emailer Cronjob
```bash
cargo run --bin emailer
```
### Webserver
```bash
cargo run --bin server
```
