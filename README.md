# geotools

I want to make a heatmap of a series of GPS paths, or just merge them and visualize tyhe result.

[Geotools](https://en.wikipedia.org/wiki/GeoTools) might be a good way to do this.

To try it out, I am following this guide:

http://docs.geotools.org/latest/userguide/tutorial/quickstart/maven.html

In order for the example to run from my WSL terminal, after a successful build, I had to
launch something called XLaunch from Xming, accepting all defaults.

Then this works ok:

```bash
export DISPLAY=:0.0
mvn exec:java -Dexec.mainClass=org.geotools.tutorial.quickstart.Quickstart
```

## Note

It's fun to use Java for a change.

But for a more web-oriented application, I may be better off looking at 
something like [Leaflet](https://en.wikipedia.org/wiki/Leaflet_(software)).
