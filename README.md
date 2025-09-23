<div align="center">
  <img src="https://avatars.githubusercontent.com/u/202675624?s=400&u=dc72a2b53e8158956a3b672f8e52e39394b6b610&v=4" alt="Flutter News App Toolkit Logo" width="220">
  <h1>Auth Client</h1>
  <p><strong>An abstract interface for authentication operations within the Flutter News App Toolkit.</strong></p>
</div>

<p align="center">
  <img src="https://img.shields.io/badge/coverage-100%25-green?style=for-the-badge" alt="coverage">
  <a href="https://flutter-news-app-full-source-code.github.io/docs/"><img src="https://img.shields.io/badge/LIVE_DOCS-VIEW-slategray?style=for-the-badge" alt="Live Docs: View"></a>
  <a href="https://github.com/flutter-news-app-full-source-code"><img src="https://img.shields.io/badge/MAIN_PROJECT-BROWSE-purple?style=for-the-badge" alt="Main Project: Browse"></a>
</p>

This `auth_client` package defines the abstract interface (`AuthClient`) for authentication operations within the [**Flutter News App Full Source Code Toolkit**](https://github.com/flutter-news-app-full-source-code). It provides a clear contract that concrete implementations (e.g., API clients, Firebase clients, in-memory mocks) must adhere to. The interface supports both an email+code password-less authentication and an anonymous authentication flow, ensuring consistent and flexible authentication mechanisms across the Flutter mobile app, web dashboard, and Dart Frog backend API.

## ⭐ Feature Showcase: Flexible & Standardized Authentication

This package offers a comprehensive set of features for managing authentication operations.

<details>
<summary><strong>🧱 Core Functionality</strong></summary>

### 🚀 Abstract `AuthClient` Interface
- **`AuthClient` Abstract Class:** Defines a generic, provider-agnostic interface for all authentication operations.
- **`authStateChanges` Stream:** A `Stream<User?>` that emits the current authenticated `User` or `null` whenever the authentication state changes (sign-in, sign-out). This is ideal for reactive UI updates.
- **`getCurrentUser()`:** An asynchronous method `Future<User?>` to retrieve the currently signed-in `User`, if any.

### 🔐 Authentication Flows
- **`requestSignInCode(String email, {bool isDashboardLogin = false})`:** Initiates the passwordless sign-in flow. It is context-aware, supporting both standard sign-in and privileged dashboard login with appropriate validation.
- **`verifySignInCode(String email, String code, {bool isDashboardLogin = false})`:** Verifies the email code to complete the sign-in/sign-up process. For dashboard login, it strictly performs a login and does not create new accounts. Returns a `Future<AuthSuccessResponse>`.
- **`signInAnonymously()`:** Signs the user in anonymously, creating a temporary user identity on the backend and returning a `Future<AuthSuccessResponse>` containing the anonymous `User` and token.
- **`signOut()`:** Signs out the current user (whether authenticated normally or anonymously).
- **`linkEmail(String email)`:** Initiates the process of linking an email to an existing anonymous account.
- **`verifyLinkEmail(String code)`:** Completes the email linking process by verifying the code. On success, it returns a `Future<AuthSuccessResponse>` with the now-permanent user and a new token.
- **`deleteAccount()`:** Allows an authenticated user to delete their own account.

### 🛡️ Standardized Error Handling
- **`HttpException` Propagation:** Implementations must map underlying errors to appropriate `HttpException` subtypes (defined in `core`), ensuring consistent and predictable error management across the application layers.

> **💡 Your Advantage:** This package provides a clear, abstract interface for authentication, decoupling your application from specific authentication service providers. This design promotes flexibility, testability, and maintainability, allowing you to easily integrate and swap authentication solutions as needed, while ensuring consistent user management and error handling.

</details>

## 🔑 Licensing

This `auth_client` package is an integral part of the [**Flutter News App Full Source Code Toolkit**](https://github.com/flutter-news-app-full-source-code). For comprehensive details regarding licensing, including trial and commercial options for the entire toolkit, please refer to the main toolkit organization page.
