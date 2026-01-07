# Service Monitor Worker (.NET)

A .NET worker service that periodically checks the health of configured URLs and logs whether each service is up or down. It uses `HttpClient` and `BackgroundService` on a schedule and is designed to be extended with database storage and alerting for real-world uptime monitoring. [web:98][web:178]

## Features

- Periodically ping multiple endpoints on independent intervals
- Record basic status: up/down, HTTP status code, timestamp, and error message
- Centralized logging for all checks
- In-memory configuration of monitored endpoints, easy to expand to a database or config file [file:160]

## Tech stack

- .NET Worker Service (`BackgroundService`, Generic Host)
- `HttpClient` for HTTP health checks
- Dependency injection for monitor and repository components [web:98][web:125]

## Project structure

- `Program.cs` – sets up the generic host, DI, and registers the worker
- `Endpoints.cs` – endpoint models and in-memory repository
- `EndpointMonitor.cs` – logic for calling each URL and building a status result
- `MonitorWorkerService.cs` – background loop that schedules and runs checks

## Quick start

1. **Clone the repo and restore**

```bash
git clone <your-repo-url>
cd MonitorWorker
dotnet restore
Run the worker

bash
dotnet run
The service will start and periodically log the health of each configured endpoint to the console. [web:98]

Configure endpoints

Edit Endpoints.cs and adjust the in-memory MonitoredEndpoint list (names, URLs, and intervals) to match the services you want to monitor. [web:178]

undefined
