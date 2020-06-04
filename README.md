# Axway-Amplify-Mesh-Init

Axway Amplify: https://platform.axway.com/
Axway Amplify Mesh Governance is a Solution to Govern multiple Service Meshes From a Unified Interface. 

The following helm chart creates:
- A Tls self signed CA secret for Istio ingress gateway
- Secrets for the Amplify Mesh Governance Service Discovery Agent and Config Sync Agent


## Create the needed namespaces
```Shell
kubectl create namespace istio-system #if not existing
kubectl create namespace apic-control #if not exisiting
```

## Run the Init
```Shell
# If you specify gatewayHost (Optional), a self signed certificate will be created for your gateway Host.
helm install https://github.com/Axway/Axway-Amplify-Mesh-Init/releases/download/1.1/Axway-Amplify-Mesh-Init-1.1.tar.gz --set gatewayHost=foo.com

```

## Run the init (Form github Repo)

```Shell
git clone https://github.com/Axway/Axway-Amplify-Mesh-Init
# If you specify gatewayHost (Optional), a self signed certificate will be created for your gateway Host. 
helm install . -n apic-init --set gatewayHost=example.com
```

## If You want to use diffrents namespaces

```Shell
kubectl create namespace foo
kubectl create namespace bar
# If you specify gatewayHost (Optional), a self signed certificate will be created for your gateway Host. 
helm install https://github.com/Axway/Axway-Amplify-Mesh-Init/releases/download/1.1/Axway-Amplify-Mesh-Init-1.1.tar.gz -n apic-init --set gatewayHost=example.com --set apic.namespace=foo --set istio.namespace=bar
```

Learn more about managing your mesh using Axway Amplify Central: https://github.com/Axway/Setup-Amplify-Mesh-Governance/wiki 
