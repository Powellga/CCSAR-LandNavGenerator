# Cochise County SAR Land Nav Course Creator

A web-based tool for creating land navigation training courses for Search and Rescue teams. Generate waypoint coordinates, bearing/distance matrices, and team-specific navigation routes for SAR training exercises.

Launch here: https://powellga.github.io/CCSAR-LandNavGenerator/

## Features

### Core Functionality
- **Waypoint Management**: Support for 4-12 waypoints with coordinate input
- **Coordinate Formats**: 
  - Degrees Decimal Minutes (DDM, default): `31 56.513, -109 57.632`
  - Decimal Degrees (DD): `31.123456, -110.123456`
- **Magnetic Declination**: Adjustable declination with East/West selection (defaults to 9.5° E for Cochise County)
- **Unit Systems**: Imperial (feet/miles, default) or Metric (meters/km)

### Team Route Generation
- **Multi-Team Support**: Configure routes for 2-10 teams
- **Points per Team**: Each team can be assigned 3-5 waypoints to find (never more than the number of waypoints on the course)
- **Course Types**:
  - **Grid Coordinate Course**: Teams find assigned points in any order
  - **Bearing/Distance Course**: Teams follow a sequential route with specific bearings and distances
- **Smart Distribution**: Every team starts at a different waypoint, every waypoint gets used, and overlap is kept as even as possible

### Calculations
- **True and Magnetic Bearings**: Both displayed for cross-reference with mapping tools
- **Distance Calculations**: Uses haversine formula for accurate geodetic calculations
- **Complete Matrix**: Full bearing/distance table between all waypoint pairs

### Output Options
- **On-Screen Display**: Formatted tables with waypoint coordinates and navigation data
- **CSV Download**: Export all course data for printing or further analysis (opens cleanly in Excel, matches what is on screen even if settings are changed afterward)
- **Save Course**: Saves the whole page, with every entry and the created course, as an .html file named after the course. Open the saved file in any browser to see the same course and team routes, edit it, download the CSV, or save it again. It works offline and the logo is built in.

## Installation

1. Download `index.html` to your local machine or web server
2. Open `index.html` in any modern web browser

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
4. **Choose Units**: Select imperial or metric measurements
5. **Enter Waypoints**: Input 4-12 coordinate points for your course

### Creating Team Routes
1. **Select Course Type**:
   - Grid Coordinate: Teams navigate to points in any order
   - Bearing/Distance: Teams follow a specific sequential route
2. **Configure Teams**: Choose 2-10 teams (cannot exceed number of waypoints)
3. **Set Points per Team**: Assign 3-5 waypoints for each team to find (limited to the number of waypoints)
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
- Alternative: `-110.123456, 31.123456` (lon, lat - auto-detected when the first value is over 90)
- A space instead of the comma also works

#### Degrees Decimal Minutes (DDM)
- Standard: `31 56.513, -109 57.632`
- With symbols: `31° 56.513', -109° 57.632'`
- With hemispheres: `N31 56.513, W109 57.632` (hemisphere letters may come before or after, upper or lower case)
- Minutes must be under 60

### Bearing Calculations
- Uses great circle (shortest path) calculations
- True bearings calculated first, then adjusted for magnetic declination
- Magnetic Bearing = True Bearing - Declination (for East declination)

### Team Distribution Algorithm
The waypoints are shuffled each time a course is created, then:
- **Enough waypoints for everyone** (teams x points per team <= waypoints): each team gets its own set with no overlap.
- **Not enough waypoints**: team starting positions are spaced evenly around the shuffled list and each team takes the next points in order. Every team starts at a different waypoint, every waypoint is used, and no waypoint is used more than one time more than any other.
- Example with 12 waypoints, 4 teams, 4 points each (before shuffling): A-B-C-D, D-E-F-G, G-H-I-J, J-K-L-A
- **Bearing/Distance courses**: after a team's start point is set, the rest of its points are put in nearest-next order to keep legs short.

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
- Points per team cannot exceed number of waypoints
- Two waypoints cannot be at the same location
- Minimum 4 waypoints required

### Display Issues
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
