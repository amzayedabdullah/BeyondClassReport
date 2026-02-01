# Testing Strategy

BeyondClass employs a comprehensive testing strategy covering distinct levels of the application: **Unit Testing** for individual components and **Performance Testing** for system stability under load.

## 1. Unit & Integration Testing (Jest)
We use [Jest](https://jestjs.io/) along with [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/) to verify that individual UI components and utility functions work as expected.

### **Tech Stack**
-   **Runner**: Jest (`jest`)
-   **Environment**: `jsdom` (Simulates a browser environment for React)
-   **Utilities**: `@testing-library/react`, `@testing-library/jest-dom`

### **Test Types**
-   **Component Tests**: Checks if components render correctly (e.g., `Header`, `Footer`).
-   **Snapshots**: Ensures UI does not change unexpectedly.

### **Running Tests**
```bash
npm test
# or
npm run test
```

***

## 2. Performance Testing (K6)
We use [Grafana k6](https://k6.io/) to simulate traffic and ensure the platform can handle real-world usage.

### **Tech Stack**
-   **Tool**: k6 (Open source load testing tool)
-   **Scripts**: Located in `k6-tests/` directory.

### **Test Types**
-   **Smoke Test** (`smoke.js`): Verifies the system is up and running with minimal load.
-   **Load Test** (`load.js`): Simulates average traffic (e.g., 20 concurrent users).
-   **Stress Test** (`stress.js`): Pushes the system to its breaking point.
-   **Soak Test** (`soak.js`): Runs for a longer duration to check for memory leaks.
-   **Spike Test** (`spike.js`): Simulates sudden bursts of traffic.

### **Running Tests**
```bash
k6 run k6-tests/load.js
```
