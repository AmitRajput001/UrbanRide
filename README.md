# UrbanRide

UrbanRide is a C++ ride-booking demo. It models a small city road network, finds routes, matches available drivers to ride requests, estimates fares, and demonstrates a ride from booking through completion or cancellation.

## Features

- City represented as a weighted graph of locations and roads.
- Route search using A* with estimated remaining travel time based on straight-line distance.
- Driver matching by availability, requested vehicle type, and estimated pickup time.
- Vehicle creation for bikes, autos, sedans, and SUVs.
- Normal, surge, and pool pricing strategies.
- Ride lifecycle operations, including assigning a driver, starting a ride, adding stops, completing a ride, and cancelling a ride.

## Project layout

```text
.
├── Main.cpp              # Demo setup and example ride flows
├── CMakeLists.txt        # CMake build configuration
└── src/
    ├── domain/           # Driver, rider, and ride models
    ├── factory/          # Vehicle factory
    ├── graph/            # Locations, roads, city graph, and route results
    ├── matching/         # Driver match model
    ├── pricing/          # Pricing interface and strategies
    ├── service/           # Ride, route, matching, pricing, and notification services
    └── vehicle/          # Vehicle base class and vehicle types
```

## Build and run

### Compile directly with g++

From the project directory:

```sh
g++ -std=c++11 -Isrc Main.cpp -o UrbanRide
./UrbanRide
```

The `-Isrc` option tells the compiler where to find the project files included by `Main.cpp`. The `-o UrbanRide` option names the compiled executable `UrbanRide`.

### Build with CMake

```sh
cmake -S . -B cmake-build-debug
cmake --build cmake-build-debug
./cmake-build-debug/UberRidePlatform
```

## Demo flow

The program creates a sample network of locations in Delhi, requests a sedan ride, notifies the two nearest eligible drivers, assigns and completes the ride with an added stop, then demonstrates a second ride being cancelled after driver assignment.

## Notes

This is an educational demo rather than a production ride-booking system. Driver locations are static during the example, and the project does not include a frontend, persistent storage, or live map/location integration.
