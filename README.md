# Test services example
## Add nginx-stable helm repo
```
helm repo add nginx-stable https://helm.nginx.com/stable
```

## Add custom annotations to the *values.yml* file
```yaml
controller:
  ...
  service:
    ...
    ## The annotations of the Ingress controller service.
    annotations:
      nato-ist/id: "1234"
      nato-ist/name: "maritime-service-radar"
      nato-ist/description: "Radar service provided by the Government of Canada"
      nato-ist/keywords: "radar;diameter;coverage;map;download"
      nato-ist/provenance: "LOCAL"
      nato-ist/contact-name: "John Smith"
      nato-ist/contact-country: "Canada"
      nato-ist/contact-email: "john.smith@canada.gov"
      nato-ist/resources: "[{\"name\":\"GetAllRadars\",\"description\":\"Retrieve all radars available\",\"digitalResourceType\":\"NONE\",\"endpoint\":{\"host\":\"my.example.com\",\"port\":8080,\"path\":\"\/radar\"}},{\"name\":\"UpdateRadarCoverage\",\"description\":\"Modifies the radar coverage diameter\",\"digitalResourceType\":\"NONE\",\"endpoint\":{\"host\":\"my.example.com\",\"port\":8080,\"path\":\"\/radar\"}},{\"name\":\"DownloadMapOfRadars\",\"description\":\"Download map of radar locations\",\"digitalResourceType\":\"STATIC\",\"uri\":\"my.example.com\/link\/to\/metadata\/document\"}]"
```

## Install Helm Chart
```
helm install nginx-stable/nginx-ingress -f values-service1.yml -n test-services
```

## Upgrade Helm Chart
```
helm upgrade nginx-stable/nginx-ingress -f values-service1.yml -n test-services
```
