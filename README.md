# web-app-helm
A chart for deploying web applications to the CISL cloud with Helm

```{note}
Information required to create a Helm chart for your web application:
1. A Name for your application, this is not the URL that will be deployed but the name of the k8s objects created
2. A URL path. This also is not the full URL, just the suffix you'd like to use after `.edu`. This is typically just `/` but may be things like `/api` that correspond to endpoints on your application.
3. An FQDN. This is the full URL for your application. Currently in the CISL cloud environment we only can create names under the `.k8s.ucar.edu` domain and your FQDN should end with `.k8s.ucar.edu`. Please make sure this is unique, try to browse to it before applying, and descriptive for your application. 
4. Container image to use. This should be an image that is already built and has been pushed to a container registry that the application can pull from. By default it is set to look at docker.io so if you are using something different you need to specify that before your container registry and image name:tag
5. Container port to expose. Your containerized application will expose a port to the network in order to communicate. More often than not there is a default for the application you are using and you also have the ability to provide a specific port if you wanted. If you have run your container image locally it is usually in the URL you used to access it locally, ie. `http://127.0.0.1:8888` is running on port 8888 and would be the appropriate value to put in the Helm chart. 
```

## Using the Notebook to generate a values.yaml file
The `helm.ipynb` file utilizes ipywidgets to allow users to input fields and create their own custom chart in a more user friendly way. It will create a `values.yaml` file in the web-app directory with the values provided in the Notebook.

## Manually create a values.yaml file
If you don't want to use the Jupyter Notebook to create a new value file you can just copy the temp file in to the web-app directory and update the values inline on your own. 