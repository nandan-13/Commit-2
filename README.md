# Commit-2 Source Code Improvments 
using System;
using System.Collections.Generic;

namespace Assignment4
{
    /**
     * Library of statistical functions using Generics for different statistical
     * calculations.
     * 
     * see http://www.calculator.net/standard-deviation-calculator.html
     * for sample standard deviation calculations
     *
     * @author Joey Programmer
     */
     ///<summary>
     ///Creates a project for doing some Averge functions stastically.
     ///Will create an average number with median function too.
     /// </summary>
    public class A4
    {
        /// <summary>
        /// Will create the the average of an array.
        /// Calculates the average and outputs in boolean type.
        /// </summary>
        /// <param name="num">This will create a number with a float value.</param>
        /// <param name="negnum">This would give True or False as output.</param>
        /// In case of True the numbers will be included in finding the sum of numbers .
        /// While in False numbers will not be included in finding the sum of numbers.
        /// <returns>
        /// The average of all real numbers in boolean values.
        /// </returns>

        //Creating a new getAverage class To find out average of real numbers.
        public static double getAverage(List<double> num, bool negnum)
        {
            //Calculating the sum of real numbers.
            double Totalsum = getSum(num, negnum);
            int count = 0;
            for (int i = 0; i < num.Count; i++)
            {
                //Creating a loop for making a condititon to execute average of count.
                if (negnum || num[i] >= 0)
                {
                    count++;
                }
            }
            //Checking if values are greater than 0 or not.
            if (count == 0)
            {
                throw new ArgumentException("no values are > 0");
            }
            //Return the average of the numbers.
            return Totalsum / count;
        }
        /// <summary>
        /// Will create the the sum of an array.
        /// Calculates the sum and outputs in boolean type.
        /// </summary>
        /// <param name="num">This will create a number with a float value.</param>
        /// <param name="negnum">This would give True or False as output.</param>
        /// In case of True the numbers will be included in finding the sum of numbers .
        /// While in False numbers will not be included in finding the sum of numbers.
        /// <returns>
        /// The sum of all real numbers in boolean values.
        /// </returns>
        //Creating a new getSum class To find out sum of real numbers.
        public static double getSum(List<double> num, bool negnum)
        {
            //Creating a loop for making a condititon to execute sum of count.
            if (num.Count < 0)
            {
                throw new ArgumentException(" cannot be empty");
            }
            //Changing the output of sum to double values.
            double sum = 0.0;
            foreach (double val in num)
            {
                //Checking if values are greater than 0 or not.
                if (negnum || val >= 0)
                {
                    sum += val;
                }
            }
            //Return the sum of numbers.
            return sum;
        }
        /// <summary>
        /// Will create the the median of an array.
        /// Calculates the median and outputs in boolean type.
        /// </summary>
        /// <param name="num">This will create a number with a float value.</param>
        /// <returns>
        /// The median of all real numbers in boolean values.
        /// </returns>
        //Creating a new getMedian class To find out median of real numbers.
        public static double getMedian(List<double> num)
        {
            //Checking if values are greater than 0 or not.
            if (num.Count == 0)
            {
                throw new ArgumentException("Size of array must be greater than 0");
            }

            num.Sort();
            //Sorting the values.
            double median = num[num.Count / 2];
            //Calculationg median by applying the formula.
            if (num.Count % 2 == 0)
                median = (num[num.Count / 2] + num[num.Count / 2 - 1]) / 2;
            //Return the median of numbers.
            return median;
        }
        /// <summary>
        /// Will create the the standard deviation of an array.
        /// Calculates the Standard deviation and outputs in boolean type.
        /// </summary>
        /// <param name="num">This will create a number with a float value.</param>
        /// <returns>
        /// The standard deviation of all real numbers in boolean values.
        /// </returns>
        //Creating a new getStandardDeviation class To find out standard deviation of real numbers.
        public static double getStandardDeviation(List<double> num)
        {
            //Checking if values are greater than 1 or not.
            if (num.Count <= 1)
            {
                throw new ArgumentException("Size of array must be greater than 1");
            }
            //Define new variables for finding standard devaition
            int number = num.Count;
            double sum = 0;
            double average = getAverage(num, true);
            //Calculating the standard deviation by applying formula.
            for (int i = 0; i < number; i++)
            {
                double v = num[i];
                sum += Math.Pow(v - average, 2);
            }
            double standardDev = Math.Sqrt(sum / (number - 1));
            //REturn the Standard Deviation of numbers
            return standardDev;
        }

        // Simple set of tests that confirm that functions operate correctly
        static void Main(string[] args)
        {
            List<double> testnum = new List<double> { 2.2, 3.3, 66.2, 17.5, 30.2, 31.1 };

            Console.WriteLine("The sum of the array = {0}", getSum(testnum, true));

            Console.WriteLine("The average of the array = {0}", getAverage(testnum, true));

            Console.WriteLine("The median value of the Double data set = {0}", getMedian(testnum));

            Console.WriteLine("The sample standard deviation of the Double test set = {0}\n", getStandardDeviation(testnum));
        }
    }
}
