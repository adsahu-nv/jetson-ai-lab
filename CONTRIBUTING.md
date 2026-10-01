# Contributing to Jetson AI Lab

Jetson AI Lab is a public, community-facing project. We invite developers both inside and outside NVIDIA to publish their Jetson work here and improve the site through pull requests.

You can contribute:

- Jetson tutorials, applications, and downloadable code samples
- Community projects built with Jetson
- New or updated model pages and verified inference instructions
- Bug fixes, accessibility improvements, and website features
- Documentation corrections and troubleshooting guidance

Submit your pull request to the `main` branch. One of the project's core contributors will review it, provide feedback when needed, and merge it after the required checks pass.

## Before You Start

- Search [existing issues](https://github.com/NVIDIA-AI-IOT/jetson-ai-lab/issues) and pull requests.
- Open an issue first for large features or architecture changes.
- Keep each pull request focused on one change.
- Only submit work you have the right to contribute under the repository's [MIT License](LICENSE).
- Never include confidential information, credentials, customer data, or private NVIDIA material.

## Set Up

Install Git, Node.js 20, and npm. Fork the repository on GitHub, then:

```bash
git clone https://github.com/YOUR-GITHUB-USERNAME/jetson-ai-lab.git
cd jetson-ai-lab
git remote add upstream https://github.com/NVIDIA-AI-IOT/jetson-ai-lab.git
npm ci
npm run dev
```

The local site runs at `http://localhost:4321`.

Create a branch from the latest `main`:

```bash
git checkout main
git pull --ff-only upstream main
git checkout -b docs/your-change
```

## Where to Contribute

| Contribution | Location |
|---|---|
| Tutorials | `src/content/tutorials/` (except `applications/`) and `src/pages/tutorials/` |
| Applications | `src/content/tutorials/applications/` |
| Model pages | `src/content/models/` |
| Project Catalog entries | `src/content/projects/` |
| Benchmarks | `src/data/benchmarks.json` |
| Downloadable scripts | `public/code-samples/` |
| Homepage content | `src/content/home.json` |

### Choose the Right Content Type

Jetson AI Lab separates reusable technical guidance from complete applications and externally maintained projects:

- **Tutorials** teach a focused, reusable building block that developers can combine with other components. Examples include setting up a runtime, serving a model, optimizing memory, or integrating one Jetson capability. Tutorial instructions must add original, Jetson-specific value and be validated on the hardware and software versions they name.
- **Applications** show a complete end-to-end experience assembled from multiple building blocks, such as a conversational assistant, robotics workflow, or live vision application. Application content belongs in `src/content/tutorials/applications/` and is surfaced from the top-level `/applications/` page rather than the Tutorials index.
- **Project Catalog entries** showcase complete community projects whose canonical documentation and source live elsewhere. NVIDIA-maintained end-to-end experiences belong under Applications. Keep catalog entries concise: explain what the project demonstrates, identify supported Jetson hardware and key technologies, include representative media, and link to the canonical repository or article.

Do not reproduce an external project's README as a Jetson AI Lab tutorial or application solely to provide a different UI. A distinctive project may receive deeper coverage when Jetson AI Lab adds meaningful material that is not already available upstream, such as independently validated results, Jetson-specific integration guidance, performance analysis, troubleshooting, or reusable technical insights. Reviewers may ask contributors to consolidate overlapping examples or submit a Project Catalog entry instead.

As a quick rule:

- Teaching one reusable capability → **Tutorial**
- Combining several capabilities into a complete experience → **Application**
- Showcasing an externally maintained repository or demo → **Project Catalog**

For tutorials, follow `TUTORIAL_TEMPLATE.md` and include `authors` in the frontmatter. For model pages and inference commands, follow `docs/jetson-matrix-and-run-modal.md` and existing model examples. All content must match the schemas in `src/content/config.ts`.

Verify Jetson commands on the hardware and JetPack version you name. Include the source and methodology for benchmark claims, use meaningful image alternative text, and clearly identify anything you did not test.

Follow existing Astro, TypeScript, Tailwind, accessibility, and responsive-design patterns for code changes. Explain any new dependency in the pull request.

## Validate

Before opening a pull request, run:

```bash
npm ci
npx playwright install chromium
npm run build
```

Also review affected pages with `npm run dev`. Include screenshots for visual changes and your tested Jetson hardware/software configuration when applicable.

## Open a Pull Request

Push your branch:

```bash
git push -u origin docs/your-change
```

Open a pull request to:

```text
NVIDIA-AI-IOT/jetson-ai-lab → main
```

Describe the change, link any related issue, and list how you tested it. By submitting a pull request, you confirm that you have the right to contribute the work under the repository's MIT License.

One of our core contributors will review the pull request and may request changes. After approval and successful checks, a core contributor will merge it. You do not need direct write access.

### Signing your commits (recommended)

We recommend signing off your commits with a [Developer Certificate of Origin (DCO)](https://developercertificate.org/). The sign-off certifies that you have the right to submit the contribution under the project's license and provides a clear record of authorship. It is encouraged but not required.

Add a sign-off with the `-s` flag:

```bash
git commit -s -m "Add a Jetson setup troubleshooting section"
```

This appends a trailer matching your commit author identity:

```text
Signed-off-by: Your Name <your.email@example.com>
```

## Reporting Issues

Use [GitHub Issues](https://github.com/NVIDIA-AI-IOT/jetson-ai-lab/issues) for bugs and feature requests. Include reproduction steps, expected and actual behavior, relevant versions, and sanitized logs.

Do not report security vulnerabilities publicly. Use NVIDIA's [security vulnerability reporting process](https://www.nvidia.com/en-us/product-security/report-vulnerability/).
