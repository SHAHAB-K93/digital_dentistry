
This code defines a function named Distance that takes two points as parameters and calculates the distance between them using the Euclidean distance formula. It then rounds the distance to one decimal place and returns it.

private double Distance(Point p1, Point p2)
{
    double distance = Math.Sqrt(Math.Pow(p2.X - p1.X, 2) + Math.Pow(p2.Y - p1.Y, 2));
    return Math.Round(distance, 1);
}
To calculate the distances based on the order of points in the list and store them in the Distance list, use the following code:
List<double> distances = new List<double>();
for (int i = 0; i < points.Count; i++)
{
    for (int j = i + 1; j < points.Count; j++)
    {
        double distance = Distance(points[i], points[j]);
        distances.Add(distance);                    
    }
}
Normalizing Distance Ratios
To generate the RD list, we need to calculate the ratio of each member in the Distance list to other members, except itself, to obtain values between 0 and 1, thus normalizing them.
List<double> RD = new List<double>();

for (int i = 0; i < distances.Count; i++)
{
    double ratio = distances[i];
    if (ratio > 1)
        ratio = 1 / ratio;
    RD.Add(ratio);
}
