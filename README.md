# TravelTip: The App That Gets You Somewhere

TravelTip is an intuitive app that helps users manage and discover their favorite travel locations, offering features such as location bookmarking, map interactions, and sharing capabilities.


## Getting Started
1. Clone the repository.
2. Run the app locally using Live Server VSCode extension.
3. Interact with the map and start managing your locations!


## Key Features
- **Location Management**: Add, edit, and delete your favorite locations. Each location is saved with details like name, rating, and geographical coordinates.
- **Search & Navigation**: Search for a specific address and view it on the map. You can also pan the map to your current geo-location with ease.
- **Interactive Map**: Users can interact with the map to create locations, update them, or view details.
- **Share & Copy Locations**: Copy location URLs or share them using the Web Share API.

## Location API (CRUDL)
The app provides a Location API that allows you to perform the following actions:

- **Create**: Add a new location by clicking on the map, providing a name and a rating.
- **Read**: View details of a selected location, including name, rating, and geographic coordinates.
- **Update**: Update the rating of a location.
- **Delete**: Remove a location from the list.
- **List**: Display a list of locations with the ability to filter, sort, and group them.

## Selected Location
When a location is selected, the following features are displayed:

- **Header**: The location name and rating are displayed at the top of the screen.
- **Active State**: The selected location is highlighted in gold in the list for easy identification.
- **Marker**: A marker is placed on the map indicating the location.
- **URL Reflection**: The location's information is reflected in the URL query parameters.
- **Copy & Share**: Users can copy the location URL to the clipboard or share it via the Web Share API.

## Location Object Format
Each location in the app is represented by an object with the following structure:

```js
{
    id: 'GEouN',
    name: 'Dahab, Egypt',
    rate: 5,
    geo: {
        address: 'Dahab, South Sinai, Egypt',
        lat: 28.5096676,
        lng: 34.5165187,
        zoom: 11
    },
    createdAt: 1706562160181,
    updatedAt: 1706562160181
}
```

- `id`: A unique identifier for the location.
- `name`: The name of the location.
- `rate`: A user-given rating for the location.
- `geo`: Geographical details including address, latitude, longitude, and zoom level.
- `createdAt`: Timestamp of when the location was created.
- `updatedAt`: Timestamp of when the location was last updated.

## Services
The app makes use of two main services: **locService** for managing locations, and **mapService** for map interactions.

### locService
Handles location-related operations:
```js
export const locService = {
    query,            // Retrieve a list of locations.
    getById,          // Get details of a single location by ID.
    remove,           // Delete a location.
    save,             // Save a new or updated location.
    setFilterBy,      // Apply filters on the location list.
    setSortBy,        // Sort locations.
    getLocCountByRateMap // Get count of locations grouped by rating.
}
```

### mapService
Handles map-related operations:
```js
export const mapService = {
    initMap,          // Initialize the map.
    getPosition,      // Get the user's current geo-location.
    setMarker,        // Place a marker on the map.
    panTo,            // Pan the map to a specific location.
    lookupAddressGeo, // Look up geographic coordinates from an address.
    addClickListener  // Add click event listener to the map.
}
```

## Controller
Functions that interact with the DOM are defined on the `window.app` object for easy access.

```js
window.app = {
    onRemoveLoc,     // Handler to remove a location.
    onUpdateLoc,     // Handler to update a location's rating.
    onSelectLoc,     // Handler to select a location from the list.
    onPanToUserPos,  // Handler to pan the map to the user's current position.
    onSearchAddress, // Handler to search for an address.
    onCopyLoc,       // Handler to copy location URL to clipboard.
    onShareLoc,      // Handler to share location via Web Share API.
    onSetSortBy,     // Handler to set sorting criteria for the location list.
    onSetFilterBy    // Handler to apply filters on the location list.
}
```

### Sample Usage

To enable user interactions, you can bind buttons to the app's functionality. Here’s an example of how to use the `onCopyLoc` and `onShareLoc` methods:

```html
<button onclick="app.onCopyLoc()">Copy Location</button>
<button onclick="app.onShareLoc()">Share Location</button>
```
