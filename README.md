# Setting Up a Helm Chart Repository on GitHub Pages

## **1. Create a Helm Chart**
Generate a Helm chart (if not created already):

```sh
helm create my-chart
cd my-chart
```

## **2. Package the Helm Chart**
Package your Helm chart into a `.tgz` file:

```sh
helm package my-chart
```

## **3. Generate the Index File**
Create an `index.yaml` file to serve as the Helm repository index:

```sh
helm repo index .
```

## **4. Push to GitHub**
Move the packaged chart (`.tgz`) and `index.yaml` to a GitHub repository (`gh-pages` branch):

```sh
git init
git checkout -b gh-pages
git add .
git commit -m "Added Helm chart repository"
git remote add origin https://github.com/suryaprakash-r/blog-app-helm.git
git push origin gh-pages
```

## **5. Enable GitHub Pages**
1. Go to your GitHub repository.
2. Navigate to **Settings > Pages**.
3. Select `gh-pages` as the source and save.
4. Your Helm repository will be available at:
   
   ```
   https://suryaprakash-r.github.io/blog-app-helm/
   ```

## **6. Add Helm Repository**
Now, add your repository to Helm:

```sh
helm repo add my-chart https://suryaprakash-r.github.io/blog-app-helm/
helm repo update
```

## **7. Verify the Setup**
Check if your Helm repository is accessible by opening:

```
https://suryaprakash-r.github.io/blog-app-helm/index.yaml
```

If it's missing, regenerate `index.yaml` and push again:

```sh
helm repo index .
git add index.yaml
git commit -m "Updated Helm repo index"
git push origin gh-pages
```

## **8. Install the Chart**
Once the repo is added, install the chart using:

```sh
helm install my-release my-chart
```

🚀 Your custom Helm chart repository is now live!
