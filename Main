using System;
using System.Collections.Generic;

namespace Recognizer
{
    public static class ThresholdFilterTask
    {
        public static double[,] ThresholdFilter(double[,] original, double whitePixelsFraction)
        {
            var height = original.GetLength(0);
            var width = original.GetLength(1);

            var pixels = new List<double>();
            for (int y = 0; y < height; y++)
                for (int x = 0; x < width; x++)
                    pixels.Add(original[y, x]);

            pixels.Sort();

            var totalPixels = pixels.Count;

            int whitePixelsCount = (int)(whitePixelsFraction * totalPixels);

            double threshold;

            if (whitePixelsCount <= 0)
            {
                threshold = double.MaxValue;
            }
            else if (whitePixelsCount >= totalPixels)
            {
                threshold = double.MinValue;
            }
            else
            {
                threshold = pixels[totalPixels - whitePixelsCount];
            }

            var result = new double[height, width];

            for (int y = 0; y < height; y++)
            {
                for (int x = 0; x < width; x++)
                {
                    if (original[y, x] >= threshold)
                        result[y, x] = 1.0;
                    else
                        result[y, x] = 0.0;
                }
            }

            return result;
        }
    }
}



