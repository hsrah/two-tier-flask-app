##### How to Install helm in Ubuntu

```
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
```

##### Important Helm Commands

- `helm create [CHART]`: Scaffold a new Helm chart.
- `helm package [CHART]`: Package the chart into a chart archive.
- `helm install [NAME] [CHART]`: Install a Helm chart.
- `helm upgrade [NAME] [CHART]`: Upgrade an installed Helm chart.
- `helm uninstall [NAME]`: Uninstall an installed Helm chart.
- `helm list`: List all installed Helm charts.
- `helm rollback [NAME] [REVISION]`: Roll back a release to a specific revision.

#### Section 3: Create Helm Chart Structure

Run the following command to scaffold a new Helm chart:

```bash
helm create mysql-chart
```

#### Section 4: Chart Metadata (`Chart.yaml`)

Open `Chart.yaml` and modify it for your application:

```yaml
apiVersion: v2
name: mysql-chart
description: A Helm chart for a mysql database
version: 0.1.0
```

#### Section 5: Default Values (`values.yaml`)

Edit `values.yaml` to include:

```yaml
replicaCount: 1

image:
  repository: mysql
  tag: latest
  pullPolicy: IfNotPresent

service:
  type: NodePort
  port: 3306
  
```

#### Section 8: Deploying the Helm Chart

Use these commands to package and deploy the chart:

```bash
# Package the chart (Optional)
helm package mysql-chart

# Deploy the chart
helm install mysql-db ./mysql-chart
```

#### Section 9: List the Deployment
```bash
# list the charts (Optional)
helm list

# Check the status
helm status <chart name>
```
