using System;

namespace TestTime
{
    public struct Time
    {
        private readonly int minutes;

        public Time(int hh, int mm)
        {
            this.minutes = 60 * hh + mm;
        }

        public int Hour
        {
            get { return minutes / 60; }
        }

        public int Minute
        {
            get { return minutes % 60; }
        }

        // ToString method 
        public override string ToString()
        {
            return String.Format("{0:D2}:{1:D2}", Hour, Minute);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Create and print Time 
            Time time1 = new Time(23, 45);
            Time time2 = new Time(10, 5);
            Time time3 = new Time(0, 0);

            Console.WriteLine("Time 1: " + time1); // Output: 23:45
            Console.WriteLine("Hour: " + time1.Hour); // Output: 23
            Console.WriteLine("Minute: " + time1.Minute); // Output: 45

            Console.WriteLine("Time 2: " + time2); // Output: 10:05
            Console.WriteLine("Time 3: " + time3); // Output: 00:00
        }
    }
}
