public class GameSession
{
    public World CurrentWorld { get; set; }
    public Location CurrentLocation { get; set; }

    public void MoveNorth()
    {
        if (HasLocationToNorth())
        {
            CurrentLocation = CurrentWorld.LocationAt(CurrentLocation.XCoordinate, CurrentLocation.YCoordinate + 1);
            OnPropertyChanged(nameof(CurrentLocation));
        }
    }

    public void MoveSouth()
    {
        if (HasLocationToSouth())
        {
            CurrentLocation = CurrentWorld.LocationAt(CurrentLocation.XCoordinate, CurrentLocation.YCoordinate - 1);
            OnPropertyChanged(nameof(CurrentLocation));
        }
    }

    public void MoveEast()
    {
        if (HasLocationToEast())
        {
            CurrentLocation = CurrentWorld.LocationAt(CurrentLocation.XCoordinate + 1, CurrentLocation.YCoordinate);
            OnPropertyChanged(nameof(CurrentLocation));
        }
    }

    public void MoveWest()
    {
        if (HasLocationToWest())
        {
            CurrentLocation = CurrentWorld.LocationAt(CurrentLocation.XCoordinate - 1, CurrentLocation.YCoordinate);
            OnPropertyChanged(nameof(CurrentLocation));
        }
    }

    private bool HasLocationToNorth()
    {
        // Check if there is a valid location to the north
        return CurrentWorld.IsValidLocation(CurrentLocation.XCoordinate, CurrentLocation.YCoordinate + 1);
    }

    private bool HasLocationToSouth()
    {
        // Check if there is a valid location to the south
        return CurrentWorld.IsValidLocation(CurrentLocation.XCoordinate, CurrentLocation.YCoordinate - 1);
    }

    private bool HasLocationToEast()
    {
        // Check if there is a valid location to the east
        return CurrentWorld.IsValidLocation(CurrentLocation.XCoordinate + 1, CurrentLocation.YCoordinate);
    }

    private bool HasLocationToWest()
    {
        // Check if there is a valid location to the west
        return CurrentWorld.IsValidLocation(CurrentLocation.XCoordinate - 1, CurrentLocation.YCoordinate);
    }

    // Implement OnPropertyChanged method here
}
