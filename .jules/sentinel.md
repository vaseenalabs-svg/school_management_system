## 2026-11-07 - Add Standard Security Headers to Next.js App
**Vulnerability:** Next.js application routes served pages and responses without essential defense-in-depth security headers (X-Frame-Options, X-Content-Type-Options, Referrer-Policy, Permissions-Policy), leaving frontend interfaces vulnerable to clickjacking and MIME sniffing.
**Learning:** While the FastAPI backend configured security headers via middleware, the Next.js frontend proxy/server was serving frontend assets and pages without them. Security headers must be configured at the frontend boundary layer (`next.config.ts`) as well.
**Prevention:** Configure security headers in Next.js `headers()` configuration covering `/:path*` to guarantee all rendered pages and API responses carry baseline HTTP security headers.
