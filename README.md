# Demo: Pebble in a rock - ASP.NET + .NET Monitor combo

> This is a demonstration project and shouldn't be used, as is, for production
> environments.

**Reference**: the ASP.NET sample in this project has been taken from the
[upstream dotnet-docker repo](https://github.com/dotnet/dotnet-docker/tree/334580f27f92b87a54fd7f46ee46a6557a26bf86/samples/aspnetapp/aspnetapp).

## Build the rock

1. [install Rockcraft](https://canonical-rockcraft.readthedocs-hosted.com/en/latest/how-to/get-started/)
2. run `rockcraft clean` and then `rockcraft pack -v`
3. if successful, you'll get the rock file `demo_latest_amd64.rock`

## Testing the container

1. copy the rock file to the Docker daemon, via `skopeo copy
oci-archive:demo_latest_amd64.rock docker-daemon:demo:latest`
2. run the container:

```bash
docker run --rm -p 8080:8080 -p 52325:52325 -p 52323:52323 demo
```

You'll then find the ASP.NET sample running at http://localhost:8080,
the .NET monitor running at http://localhost:52323, and the .NET
monitor metrics available at http://localhost:52325.
