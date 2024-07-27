// Define the list of points
List<Point> points = new List<Point>();
points.Add(Na);
points.Add(S);
points.Add(Or);
points.Add(ANS);
points.Add(PNS);
points.Add(Ar);
points.Add(Go);
points.Add(Me);

// Define the list of intermediate points
List<Point> intermediatePoints = new List<Point>();

Point previousPoint = points[0]; // Consider the previous point as the first point

for (int index = 1; index < points.Count; index++)
{
    Point currentPoint = points[index];

    int Xm = (previousPoint.X + currentPoint.X) / 2;
    int Ym = (previousPoint.Y + currentPoint.Y) / 2;

    Point intermediatePoint = new Point { X = Xm, Y = Ym };
    intermediatePoints.Add(intermediatePoint);

    for (int i = 1; i <= n; i++)
    {
        int Xn = previousPoint.X + (currentPoint.X - previousPoint.X) * i / (n + 1);
        int Yn = previousPoint.Y + (currentPoint.Y - previousPoint.Y) * i / (n + 1);

        Point newLandmark = new Point { X = Xn, Y = Yn };
        intermediatePoints.Add(newLandmark);
    }

    previousPoint = currentPoint;
}

List<Point> finalLandmarks = new List<Point>();
finalLandmarks.AddRange(points);
finalLandmarks.AddRange(intermediatePoints);
