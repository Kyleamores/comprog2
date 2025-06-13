using System;

namespace TestTime
{
    public struct Time
    {
        private readonly int minutes;

        // Constructor: hh:mm
        public Time(int hh, int mm)
        {
            this.minutes = 60 * hh + mm;
        }

        // Constructor: total minutes
        public Time(int totalMinutes)
        {
            this.minutes = totalMinutes;
        }

        // Hour property
        public int Hour
        {
            get { return minutes / 60; }
        }

        // Minute property
        public int Minute
        {
            get { return minutes % 60; }
        }

        // ToString override
        public override string ToString()
        {
            return String.Format("{0:D2}:{1:D2}", Hour, Minute);
        }

        // Overload + operator
        public static Time operator +(Time a, Time b)
        {
            return new Time(a.minutes + b.minutes);
        }

        // Overload - operator
        public static Time operator -(Time a, Time b)
        {
            return new Time(a.minutes - b.minutes);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Time t1 = new Time(1, 30);     // 90 minutes
            Time t2 = new Time(2, 45);     // 165 minutes

            Time sum = t1 + t2;            // Should be 255 minutes → 04:15
            Time diff = t2 - t1;           // Should be 75 minutes → 01:15

            Console.WriteLine("Time 1: " + t1);    // 01:30
            Console.WriteLine("Time 2: " + t2);    // 02:45
            Console.WriteLine("Sum: " + sum);      // 04:15
            Console.WriteLine("Difference: " + diff); // 01:15
        }
    }
}
