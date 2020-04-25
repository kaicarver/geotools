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

You can open `countries.shp` for a display of a world map.

Listing the dependencies is interesting:

(and yeah, the WARNING every time I run anything is annoying, we'll see if I can make it go away)

```bash
(base) kai@bluesteel:~/geotools$ mvn dependency:tree
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by com.google.inject.internal.cglib.core.$ReflectUtils$1 (file:/usr/share/maven/lib/guice.jar) to method java.lang.ClassLoader.defineClass(java.lang.String,byte[],int,int,java.security.ProtectionDomain)
WARNING: Please consider reporting this to the maintainers of com.google.inject.internal.cglib.core.$ReflectUtils$1
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
[INFO] Scanning for projects...
[INFO]
[INFO] -----------------------< org.geotools:tutorial >------------------------
[INFO] Building tutorial 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-dependency-plugin:2.8:tree (default-cli) @ tutorial ---
[INFO] org.geotools:tutorial:jar:1.0-SNAPSHOT
[INFO] +- junit:junit:jar:4.11:test
[INFO] |  \- org.hamcrest:hamcrest-core:jar:1.3:test
[INFO] +- org.geotools:gt-shapefile:jar:24-SNAPSHOT:compile
[INFO] |  \- javax.media:jai_core:jar:1.1.3:compile
[INFO] +- org.geotools:gt-swing:jar:24-SNAPSHOT:compile
[INFO] |  +- org.geotools:gt-referencing:jar:24-SNAPSHOT:compile
[INFO] |  |  +- org.ejml:ejml-ddense:jar:0.34:compile
[INFO] |  |  |  \- org.ejml:ejml-core:jar:0.34:compile
[INFO] |  |  +- commons-pool:commons-pool:jar:1.5.4:compile
[INFO] |  |  +- org.geotools:gt-metadata:jar:24-SNAPSHOT:compile
[INFO] |  |  |  +- org.geotools:gt-opengis:jar:24-SNAPSHOT:compile
[INFO] |  |  |  |  \- systems.uom:systems-common-java8:jar:0.7.2:compile
[INFO] |  |  |  |     +- tec.uom:uom-se:jar:1.0.8:compile
[INFO] |  |  |  |     |  +- javax.measure:unit-api:jar:1.0:compile
[INFO] |  |  |  |     |  \- tec.uom.lib:uom-lib-common:jar:1.0.2:compile
[INFO] |  |  |  |     +- si.uom:si-quantity:jar:0.7.1:compile
[INFO] |  |  |  |     \- si.uom:si-units-java8:jar:0.7.1:compile
[INFO] |  |  |  \- org.geotools.ogc:net.opengis.ows:jar:24-SNAPSHOT:compile
[INFO] |  |  |     +- org.geotools.ogc:org.w3.xlink:jar:24-SNAPSHOT:compile
[INFO] |  |  |     +- org.eclipse.emf:org.eclipse.emf.common:jar:2.15.0:compile
[INFO] |  |  |     +- org.eclipse.emf:org.eclipse.emf.ecore:jar:2.15.0:compile
[INFO] |  |  |     \- org.eclipse.emf:org.eclipse.emf.ecore.xmi:jar:2.15.0:compile
[INFO] |  |  +- it.geosolutions.jgridshift:jgridshift-core:jar:1.3:compile
[INFO] |  |  \- net.sf.geographiclib:GeographicLib-Java:jar:1.49:compile
[INFO] |  \- com.miglayout:miglayout:jar:swing:3.7:compile
[INFO] +- org.geotools:gt-render:jar:24-SNAPSHOT:compile
[INFO] |  +- org.geotools:gt-coverage:jar:24-SNAPSHOT:compile
[INFO] |  |  +- javax.media:jai_imageio:jar:1.1:compile
[INFO] |  |  +- it.geosolutions.imageio-ext:imageio-ext-tiff:jar:1.3.2:compile
[INFO] |  |  |  +- it.geosolutions.imageio-ext:imageio-ext-utilities:jar:1.3.2:compile
[INFO] |  |  |  +- it.geosolutions.imageio-ext:imageio-ext-geocore:jar:1.3.2:compile
[INFO] |  |  |  |  +- javax.xml.bind:jaxb-api:jar:2.4.0-b180830.0359:compile
[INFO] |  |  |  |  +- it.geosolutions.imageio-ext:imageio-ext-streams:jar:1.3.2:compile
[INFO] |  |  |  |  +- org.glassfish.jaxb:jaxb-runtime:jar:2.4.0-b180830.0438:runtime
[INFO] |  |  |  |  |  +- org.glassfish.jaxb:txw2:jar:2.4.0-b180830.0438:runtime
[INFO] |  |  |  |  |  +- com.sun.istack:istack-commons-runtime:jar:3.0.7:runtime
[INFO] |  |  |  |  |  +- org.jvnet.staxex:stax-ex:jar:1.8:runtime
[INFO] |  |  |  |  |  \- com.sun.xml.fastinfoset:FastInfoset:jar:1.2.15:runtime
[INFO] |  |  |  |  \- javax.activation:javax.activation-api:jar:1.2.0:compile
[INFO] |  |  |  \- javax.media:jai_codec:jar:1.1.3:compile
[INFO] |  |  +- org.jaitools:jt-zonalstats:jar:1.5.0:compile
[INFO] |  |  +- org.jaitools:jt-utils:jar:1.5.0:compile
[INFO] |  |  +- it.geosolutions.jaiext.affine:jt-affine:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.algebra:jt-algebra:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.bandmerge:jt-bandmerge:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.bandselect:jt-bandselect:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.bandcombine:jt-bandcombine:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.border:jt-border:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.buffer:jt-buffer:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.crop:jt-crop:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.iterators:jt-iterators:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.lookup:jt-lookup:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.mosaic:jt-mosaic:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.nullop:jt-nullop:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.rescale:jt-rescale:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.scale:jt-scale:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.scale2:jt-scale2:jar:1.1.14:compile
[INFO] |  |  |  \- org.huldra.math:bigint:jar:0.7.1:compile
[INFO] |  |  +- it.geosolutions.jaiext.stats:jt-stats:jar:1.1.14:compile
[INFO] |  |  |  \- com.google.guava:guava:jar:27.0-jre:compile
[INFO] |  |  |     +- com.google.guava:failureaccess:jar:1.0:compile
[INFO] |  |  |     +- com.google.guava:listenablefuture:jar:9999.0-empty-to-avoid-conflict-with-guava:compile
[INFO] |  |  |     +- com.google.code.findbugs:jsr305:jar:3.0.2:compile
[INFO] |  |  |     +- org.checkerframework:checker-qual:jar:2.5.2:compile
[INFO] |  |  |     +- com.google.errorprone:error_prone_annotations:jar:2.2.0:compile
[INFO] |  |  |     +- com.google.j2objc:j2objc-annotations:jar:1.1:compile
[INFO] |  |  |     \- org.codehaus.mojo:animal-sniffer-annotations:jar:1.17:compile
[INFO] |  |  +- it.geosolutions.jaiext.translate:jt-translate:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.utilities:jt-utilities:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.warp:jt-warp:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.zonal:jt-zonal:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.binarize:jt-binarize:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.format:jt-format:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.colorconvert:jt-colorconvert:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.errordiffusion:jt-errordiffusion:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.orderdither:jt-orderdither:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.colorindexer:jt-colorindexer:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.imagefunction:jt-imagefunction:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.piecewise:jt-piecewise:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.classifier:jt-classifier:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.rlookup:jt-rlookup:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.vectorbin:jt-vectorbin:jar:1.1.14:compile
[INFO] |  |  +- it.geosolutions.jaiext.shadedrelief:jt-shadedrelief:jar:1.1.14:compile
[INFO] |  |  \- commons-io:commons-io:jar:2.6:compile
[INFO] |  +- org.geotools:gt-cql:jar:24-SNAPSHOT:compile
[INFO] |  \- com.conversantmedia:disruptor:jar:1.2.13:compile
[INFO] |     \- org.slf4j:slf4j-api:jar:1.7.13:compile
[INFO] \- org.geotools:gt-main:jar:24-SNAPSHOT:compile
[INFO]    +- org.locationtech.jts:jts-core:jar:1.16.1:compile
[INFO]    +- org.apache.commons:commons-text:jar:1.6:compile
[INFO]    |  \- org.apache.commons:commons-lang3:jar:3.8.1:compile
[INFO]    \- com.fasterxml.jackson.core:jackson-core:jar:2.10.1:compile
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  12.093 s
[INFO] Finished at: 2020-04-25T18:10:45+02:00
[INFO] ------------------------------------------------------------------------
```

## Note

It's fun to use Java for a change.

But for a more web-oriented application, I may be better off looking at 
something like [Leaflet](https://en.wikipedia.org/wiki/Leaflet_(software)).
