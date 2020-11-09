# TZ
решение 3 задачи


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Z3
{
    class Program
    {
        static bool IsLess(int x, int y)
        {
            if (x % 2 == 0 && y % 2 != 0)
                return true;
            if (x % 2 != 0 && y % 2 == 0)
                return false;
            if (x % 2 == 0 && y % 2 == 0)
                return x < y;
            return x > y;
        }

        static void Main(string[] args)
        {
            Console.Write("Введите N - количество чисел: ");
            var n = int.Parse(Console.ReadLine());
            Console.Write($"Введите массив из {n} чисел: ");
            var a = Console.ReadLine().Split().Select(int.Parse).ToArray();

            for(int i = 0; i < n; i++)
                for(int j = n - 1; j > i; j--)
                    if (IsLess(a[j], a[j - 1]))
                    {
                        var x = a[j];
                        a[j] = a[j - 1];
                        a[j - 1] = x;
                    }

            Console.Write("Массив после сортировки: ");
            foreach (var x in a)
                Console.Write(x + " ");
            Console.WriteLine();
        }
    }
}

