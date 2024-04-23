**Title: Enabling Inter-namespace Communication in Kubernetes using Network Policies**

**Introduction:**
This repository contains a Kubernetes Network Policy configuration aimed at facilitating secure communication between pods across namespaces. Specifically, the provided YAML file outlines the steps to allow a pod residing in the "dev" namespace to establish connections with specific ports of pods located in the "Test" namespace. Employing Kubernetes Network Policies ensures controlled ingress traffic, bolstering the security and integrity of inter-namespace interactions within the Kubernetes cluster.

**File Structure:**
- `netpol.yaml`: YAML file specifying the Network Policy configuration.

**Usage:**
1. **Applying the Network Policy:**
   Execute the following command to apply the Network Policy to your Kubernetes cluster:
   ```
   kubectl apply -f netpol.yaml
   ```

2. **Verifying Configuration:**
   After applying the Network Policy, ensure its successful implementation by examining the applied policies:
   ```
   kubectl get networkpolicy -n dev
   ```

**Configuration Details:**
- **Namespace:** `dev`
- **Policy Type:** Ingress
- **Pod Selector:** All pods within the `dev` namespace.
- **Ingress Rules:**
  - **From Namespace:** `test`
    - **Match Labels:** `name: test`
  - **Ports:** 
    - `TCP/9000`
    - `TCP/9001`
    - `TCP/9002`

**Important Notes:**
- Prior to applying the Network Policy, ensure that the `test` namespace has been labeled with `name: test`.
- Customize the port numbers in the configuration file (`port: <your_port_number>`) to match the specific port(s) you wish to enable communication with in the "Test" namespace.


