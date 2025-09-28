# Cochise County SAR Land Nav Course Creator

A web-based tool for creating land navigation training courses for Search and Rescue teams. Generate waypoint coordinates, bearing/distance matrices, and team-specific navigation routes for SAR training exercises.
https://powellga.github.io/CCSAR-LandNavGenerator/

## Features

### Core Functionality
- **Waypoint Management**: Support for 4-12 waypoints with coordinate input
- **Coordinate Formats**: 
  - Decimal Degrees (DD): `31.123456, -110.123456`
  - Degrees Decimal Minutes (DDM): `31 56.513, -109 57.632`
- **Magnetic Declination**: Adjustable declination with East/West selection (defaults to 9.5° E for Cochise County)
- **Unit Systems**: Metric (meters/km) or Imperial (feet/miles)

### Team Route Generation
- **Multi-Team Support**: Configure routes for 2-10 teams
- **Points per Team**: Each team can be assigned 3-5 waypoints to find
- **Course Types**:
  - **Grid Coordinate Course**: Teams find assigned points in any order
  - **Bearing/Distance Course**: Teams follow a sequential route with specific bearings and distances
- **Smart Distribution**: Rotation algorithm ensures teams start at different waypoints and minimizes overlap

### Calculations
- **True and Magnetic Bearings**: Both displayed for cross-reference with mapping tools
- **Distance Calculations**: Uses haversine formula for accurate geodetic calculations
- **Complete Matrix**: Full bearing/distance table between all waypoint pairs

### Output Options
- **On-Screen Display**: Formatted tables with waypoint coordinates and navigation data
- **CSV Download**: Export all course data for printing or further analysis

## Installation

1. Download `index.html` to your local machine or web server
2. Place your `CCSAR.jpg` logo file in the same directory (optional)
3. Open `index.html` in any modern web browser

### GitHub Pages Hosting
1. Create a new GitHub repository
2. Upload `index.html` and `CCSAR.jpg` to the repository
3. Enable GitHub Pages in repository settings
4. Access your course creator at `https://[username].github.io/[repository-name]`

## Usage

### Basic Course Setup
1. **Name Your Course**: Enter a descriptive name for the training exercise
2. **Select Coordinate Format**: Choose between DD or DDM based on your GPS/map preference
3. **Set Declination**: Adjust magnetic declination for your training area
4. **Choose Units**: Select metric or imperial measurements
5. **Enter Waypoints**: Input 4-12 coordinate points for your course

### Creating Team Routes
1. **Select Course Type**:
   - Grid Coordinate: Teams navigate to points in any order
   - Bearing/Distance: Teams follow a specific sequential route
2. **Configure Teams**: Choose 2-10 teams (cannot exceed number of waypoints)
3. **Set Points per Team**: Assign 3-5 waypoints for each team to find
4. **Generate Course**: Click "Create Course" to generate routes and navigation data

### Understanding the Output

#### Waypoint Table
- Lists all course waypoints with their coordinates in your selected format

#### Bearing and Distance Matrix
- **True Bearing (°T)**: For use with maps and CalTopo
- **Magnetic Bearing (°M)**: For field navigation with compass
- **Distances**: Shown in your selected unit system

#### Team Routes
- **Grid Course**: Each team receives a unique set of waypoints to find
- **Bearing/Distance Course**: Sequential navigation instructions with:
  - Starting waypoint and coordinates
  - Leg-by-leg bearings and distances
  - Total route distance

## Technical Details

### Coordinate Input Formats

#### Decimal Degrees (DD)
- Standard: `31.123456, -110.123456` (lat, lon)
- Alternative: `-110.123456, 31.123456` (lon, lat - auto-detected)

#### Degrees Decimal Minutes (DDM)
- Standard: `31 56.513, -109 57.632`
- With symbols: `31° 56.513', -109° 57.632'`
- With hemispheres: `N31 56.513, W109 57.632`

### Bearing Calculations
- Uses great circle (shortest path) calculations
- True bearings calculated first, then adjusted for magnetic declination
- Magnetic Bearing = True Bearing - Declination (for East declination)

### Team Distribution Algorithm
The app uses a rotation pattern to distribute waypoints:
- Each team starts at a different waypoint
- Points are distributed to minimize position overlap
- Example with 4 waypoints (A,B,C,D) and 4 teams:
  - Team 1: A→B→C→D
  - Team 2: B→C→D→A
  - Team 3: C→D→A→B
  - Team 4: D→A→B→C

## Browser Compatibility
- Chrome (recommended)
- Firefox
- Safari
- Edge
- Mobile browsers (iOS Safari, Chrome Mobile)

## Troubleshooting

### Coordinate Input Errors
- Ensure coordinates are in the correct format for your selection
- Verify latitude values are between -90 and 90
- Verify longitude values are between -180 and 180
- Check for typos in degree symbols or hemisphere indicators

### Team Configuration Issues
- Number of teams cannot exceed number of waypoints
- Each team needs a unique starting position
- Minimum 4 waypoints required

### Display Issues
- If the logo doesn't appear, ensure `CCSAR.jpg` is in the same folder as `index.html`
- For best results, use a modern browser with JavaScript enabled

## Support

For issues, questions, or suggestions about this tool, contact:

**Gregg Powell**  
Cochise County SAR R-83  
Email: g.a.powell@protonmail.com

## License

Created for Cochise County Sheriff Search and Rescue training operations.

## Acknowledgments

Developed specifically for SAR training exercises in Cochise County, Arizona, with default magnetic declination set for the local area.
