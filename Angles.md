Calculating the Angle Between Three Landmarks
This code calculates the angle between three points in degrees. The function uses the dot product formula to find the angle between two vectors.

csharp
Copy code
private double AngleFrom3PointsInDegrees(Point p1, Point p2, Point p3)
{
    Point A = new Point();
    A.X = p1.X - p2.X;
    A.Y = p1.Y - p2.Y;
    Point B = new Point();
    B.X = p3.X - p2.X;
    B.Y = p3.Y - p2.Y;

    double ALen = Math.Sqrt(Math.Pow(A.X, 2) + Math.Pow(A.Y, 2));
    double BLen = Math.Sqrt(Math.Pow(B.X, 2) + Math.Pow(B.Y, 2));
    double dotProduct = A.X * B.X + A.Y * B.Y;
    double theta = (180 / Math.PI) * Math.Acos(dotProduct / (ALen * BLen));
    return Math.Round(theta, 1);
}
