# TLS Point Cloud Registration and Coordinate Transformation

This project demonstrates how multiple terrestrial laser scanner (TLS) scans can be combined into single 3D point cloud and transformed into global coordinate system.

1. Convert raw TLS measurements from spherical coordinates to Cartesian coordinates.
2. Register multiple scans into one local coordinate frame.
3. Transform the merged point cloud into the WGS84 global coordinate system.
4. Convert coordinates into the Earth-Centered Earth-Fixed (ECEF) frame.

### A terrestrial laser scanner records points using:

* Distance (d)
* Horizontal angle (θ)
* Vertical angle (φ)

But these measurements are not directly used for point cloud processing.

To combine scans from different scanner positions, all points must first be converted into Cartesian coordinates and then transformed into a common reference frame.


### Spherical to Cartesian Conversion

Each laser measurement is converted into a 3D point:

x = d × cos(φ) × cos(θ)

y = d × cos(φ) × sin(θ)

z = d × sin(φ)

After conversion, every scan is stored as point cloud containing XYZ coordinates.

### Scan Registration

Each scanner has its own local coordinate system and then combine all to whole pointcloud

* Use the transformation parameters from data
* Transform S1, S2, and S3 into the coordinate frame of S4.
* Apply the transformations iteratively.
* Merge the transformed point clouds https://github.com/prasanna1511/TLS-Point-Cloud-Registration-and-Coordinate-Transformation/blob/main/complete_registration.png.

### Transformation to WGS84

The merged point cloud is transformed from the local S4 frame to the global WGS84 coordinate system.

A globally referenced point cloud.

The WGS84 coordinates are converted to:

### Geographic Validation

The final coordinates are checked using:

* Google Maps https://github.com/prasanna1511/TLS-Point-Cloud-Registration-and-Coordinate-Transformation/blob/main/google_map.png
* Google Earth

The estimated location corresponds to:

Latitude: 50.7276171

Longitude: 7.0867992

Altitude: 108.50 m


### Tools Used

* Python
* NumPy
* Open3D
* CloudCompare
* Google Earth
* Google Maps

## Author

Prasanna Bijja
