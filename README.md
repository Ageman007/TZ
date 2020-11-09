# TZ 1
решение 3 задач 


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Z1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Введите строку: ");
            var str = Console.ReadLine();
            Console.Write("Введите новую подстроку: ");
            var substr = Console.ReadLine();

            int balance = 0, firstIndex = -1, lastIndex = -1;
            for(int i = 0; i < str.Length; i++)
            {
                if (str[i] == '[')
                {
                    if (balance == 0)
                        firstIndex = i;
                    balance++;
                }
                if (str[i] == ']')
                {
                    if (balance > 0)
                    {
                        balance--;
                        if (balance == 0)
                        {
                            lastIndex = i;
                            break;
                        }
                    }
                }
            }

            if (firstIndex == -1)
                Console.WriteLine("В строке нет открывающих квадратных скобок");
            else if (lastIndex == -1)
                Console.WriteLine("В строке нет закрывающей скобки, которая соответствует первой открывающей");
            else if (firstIndex != -1 && lastIndex != -1)
            {
                str = str.Remove(firstIndex, lastIndex - firstIndex + 1);
                str = str.Insert(firstIndex, substr);
                Console.WriteLine($"Строка после замены выражения в квадратных скобках на новую подстроку: {str}");
            }
        }
    }
}
