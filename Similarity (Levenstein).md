Calculating the Similarity of Two Strings
This code defines a function that calculates the Levenshtein distance between two strings. This algorithm calculates the minimum number of edits needed to transform one string into another.

Initial Checks: It first checks whether both input strings are valid. If either of them is invalid, it returns zero.
Handling Empty Strings: If the length of one of the strings is zero, it returns the length of the other string.
Creating Distance Matrix: A distance matrix with dimensions similar to the input strings is created.
Calculating Levenshtein Distance: Using nested loops and comparing the characters of the strings, the Levenshtein distance is computed.
Returning the Distance: Finally, the Levenshtein distance between the two strings is returned.


int ComputeLevenshteinDistance(string source, string target)
{
    if ((source == null) || (target == null)) return 0;
    if ((source.Length == 0) || (target.Length == 0)) return 0;
    if (source == target) return source.Length;

    int sourceWordCount = source.Length;
    int targetWordCount = target.Length;

    // Step 1
    if (sourceWordCount == 0)
        return targetWordCount;

    if (targetWordCount == 0)
        return sourceWordCount;

    int[,] distance = new int[sourceWordCount + 1, targetWordCount + 1];

    // Step 2
    for (int i = 0; i <= sourceWordCount; distance[i, 0] = i++) ;
    for (int j = 0; j <= targetWordCount; distance[0, j] = j++) ;

    for (int i = 1; i <= sourceWordCount; i++)
    {
        for (int j = 1; j <= targetWordCount; j++)
        {
            // Step 3
            int cost = (target[j - 1] == source[i - 1]) ? 0 : 1;

            // Step 4
            distance[i, j] = Math.Min(Math.Min(distance[i - 1, j] + 1, distance[i, j - 1] + 1), distance[i - 1, j - 1] + cost);
        }
    }

    return distance[sourceWordCount, targetWordCount];
}


double CalculateSimilarity(string source, string target)
{
    if ((source == null) || (target == null)) return 0.0;
    if ((source.Length == 0) || (target.Length == 0)) return 0.0;
    if (source == target) return 1.0;

    int stepsToSame = ComputeLevenshteinDistance(source, target);
    return (1.0 - ((double)stepsToSame / (double)Math.Max(source.Length, target.Length)));
}
