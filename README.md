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

        public Time(int totalMinutes)
        {
            this.minutes = totalMinutes;
        }

        public int Hour => minutes / 60;
        public int Minute => minutes % 60;

        public override string ToString()
        {
            return String.Format("{0:D2}:{1:D2}", Hour, Minute);
        }

        public static Time operator +(Time a, Time b)
        {
            return new Time(a.minutes + b.minutes);
        }

        public static Time operator -(Time a, Time b)
        {
            return new Time(a.minutes - b.minutes);
        }


        public static implicit operator Time(int totalMinutes)
        {
            return new Time(totalMinutes);
        }


        public static explicit operator int(Time time)
        {
            return time.minutes;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // conversion from int
            Time t1 = 90; // 01:30
            Time t2 = 135; // 02:15

            // conversion to int
            int totalMinutes1 = (int)t1;
            int totalMinutes2 = (int)t2;

            Console.WriteLine("Time 1: " + t1);         // Output: 01:30
            Console.WriteLine("Time 2: " + t2);         // Output: 02:15
            Console.WriteLine("Total Minutes 1: " + totalMinutes1); // Output: 90
            Console.WriteLine("Total Minutes 2: " + totalMinutes2); // Output: 135
        }
    }
}
