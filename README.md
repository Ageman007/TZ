# TZ2
решение 2 задачи 

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Z2
{
    class Program
    {
        static bool IsPalindrome(List<int> digits)
        {
            for (int i = 0; i < digits.Count / 2; i++)
                if (digits[i] != digits[digits.Count - i - 1])
                    return false;
            return true;
        }

        static void Main(string[] args)
        {
            Console.Write("Введите число: ");
            var x = int.Parse(Console.ReadLine());
            var digits = new List<int>();
            if (x == 0)
                digits.Add(0);
            while(x > 0)
            {
                digits.Add(x % 10);
                x /= 10;
            }
            if (x == 0 && IsPalindrome(digits))
                Console.WriteLine($"Число является палиндромом");
            else
                Console.WriteLine($"Число не является палиндромом");
        }
    }
}
