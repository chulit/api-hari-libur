# API Hari Libur Indonesia

This repository contains a Deno-based API application that provides information
about public holidays in Indonesia. The holiday data is sourced from
[tanggalans.com](https://www.tanggalans.com/), offering up-to-date and accurate
information.

## Usage

### Prerequisites

Ensure that you have Deno installed on your machine. You can install Deno by
following the instructions on the official Deno website:
[Deno Installation](https://deno.land/#installation).

### Getting Started

1. Clone the repository:

   ```bash
   git clone https://github.com/radyakaze/api-hari-libur.git
   ```

2. Change into the project directory:

   ```bash
   cd api-hari-libur
   ```

3. Run the application:

   ```bash
   deno task dev
   ```

   This command will start the Deno application, and the API will be accessible
   at `http://localhost:8000`.

### API Demo

You can also explore a live demo of the API at
[libur.deno.dev](https://libur.deno.dev).

## Deployment

This application is ready to deploy on **Deno Deploy**.

### Option 1: Direct GitHub Integration (Deno Deploy Web Dashboard)
1. Go to [dash.deno.com](https://dash.deno.com) and create a new project.
2. Connect your GitHub repository `api-hari-libur`.
3. Set the Entrypoint to `src/main.ts`.
4. **Attach KV Database:** Go to project settings -> **KV** tab -> Click **Create Database** (or Attach Database).
5. Click **Deploy**. Automatic deployments will be triggered whenever you push to the `main` branch.

### Option 2: GitHub Actions Workflow
This repository includes a `.github/workflows/deploy.yml` CI/CD workflow:
1. Ensure your project in Deno Deploy has a KV database created under the **KV** tab.
2. Ensure your repository secret `DENO_DEPLOY_TOKEN` is set if using `deployctl`.
3. Push your changes to `main` branch to trigger automatic code formatting checks, linting, and deployment.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file
for details.

## Acknowledgments

- The holiday data is sourced from [tanggalans.com](https://www.tanggalans.com/).
- Special thanks to the Deno community for providing a robust and secure
  runtime.

Feel free to contribute to this project or use it in your applications! If you
encounter any issues or have suggestions for improvement, please open an issue
on GitHub.
