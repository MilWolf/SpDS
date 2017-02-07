# SpDS

Spatial data structures to speed up the searches.

Installation with Maven
=

Add the following repository :

```xml
<repository>
    <id>amap-maven-central</id>
    <name>libs-release</name>
    <url>http://manosque.cirad.fr:8081/artifactory/libs-release-local</url>
</repository>
```

And the following dependency:

```xml
<dependency>
    <groupId>fr.amap.lidar</groupId>
    <artifactId>format-spds</artifactId>
    <version>1.0.0</version>
</dependency>
```

Usage
=

```java
//create an octree with a maximum number of points of 50 for a leaf node
Octree<Point3D> octree = new Octree(50);

//set array of points
octree.setPoints(new Point3D[]{});

try {
    //don't forget to build the octree
    octree.build();
    
    //search the closest point of the given point within the given search radius
    Point3D nearestPoint = octree.searchNearestPoint(new Point3D(5.0, 1.0, 6), Octree.INCREMENTAL_SEARCH, 0.0001f);
    if(nearestPoint != null){
        System.out.println("Point found : ("+ nearestPoint.x+" "+nearestPoint.y+" "+nearestPoint.z+")");
    }
    
} catch (Exception ex) {
    Logger.getLogger(Octree.class.getName()).log(Level.SEVERE, null, ex);
}
```
