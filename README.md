# Helm

```sh
helm repo index . --url https://vdmpo.github.io/helm/
git add .
gc 'consul 1.9.0-1'
git push origin
```

### Alternative ways

```sh
cd mychart/
helm package .
curl --data-binary "@mychart-0.1.0.tgz" http://localhost:8080/api/charts
```

or

```sh
helm push mychart/ chartmuseum
```
