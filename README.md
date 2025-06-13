# comprog2
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

        public override string ToString()
        {
            int hh = minutes / 60;
            int mm = minutes % 60;
            return $"{hh:D2}:{mm:D2}";
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Time time1 = new Time(10, 5);
            Time time2 = new Time(0, 45);
            Time time3 = new Time(23, 59);

            Console.WriteLine("Time 1: " + time1);  // Expected: 10:05
            Console.WriteLine("Time 2: " + time2);  // Expected: 00:45
            Console.WriteLine("Time 3: " + time3);  // Expected: 23:59
        }
    }
}
