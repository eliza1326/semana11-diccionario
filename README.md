# semana11-diccionario
Uso de diccionario, con la plicacion de un diccionario ingles y español
Link de ejecucion del codigo en C#: https://www.programiz.com/online-compiler/2kN0YMTZ8ALqF

using System;
using System.Collections.Generic;

class Traductor
{
    static Dictionary<string, string> diccionario = new Dictionary<string, string>()
    {
        {"flower", "flor"}, {"hands", "manos"}, {"red", "rojo"}, {"love", "amor"},
        {"white", "blanco"}, {"peace", "paz"}, {"women", "mujer"}, {"yelow", "amarillo"},
        {"life", "vida"}, {"gift", "regalo"}, {"give", "dar"}, {"child", "niño"},
        {"eye", "ojo"}, {"woman", "mujer"}, {"place", "lugar"}, {"garden", "jardín"},
        {"day", "día"}, {"street", "calle"}, {"house", "casa"}, {"anywhere", "cualquier/a"},
        {"pink", "rosado"}, {"i", "yo"}, {"a", "una"}, {"girl", "chica"}, {"in", "en"}
    };

    static void Main()
    {
        int opcion;
        do
        {
            Console.WriteLine("\nMENU");
            Console.WriteLine("=======================================================");
            Console.WriteLine("1. Traducir una frase");
            Console.WriteLine("2. Ingresar más palabras al diccionario");
            Console.WriteLine("0. Salir");
            Console.Write("Seleccione una opción: ");
            opcion = Convert.ToInt32(Console.ReadLine());

            switch (opcion)
            {
                case 1:
                    TraducirFrase();
                    break;
                case 2:
                    AgregarPalabra();
                    break;
                case 0:
                    Console.WriteLine("Saliendo del programa...");
                    break;
                default:
                    Console.WriteLine("Opción inválida, intente nuevamente.");
                    break;
            }
        } while (opcion != 0);
    }

    static void TraducirFrase()
    {
        Console.Write("\nIngrese la frase a traducir: ");
        string frase = Console.ReadLine();
        string[] palabras = frase.Split(' ');

        for (int i = 0; i < palabras.Length; i++)
        {
            string palabra = palabras[i].ToLower();

            if (diccionario.ContainsKey(palabra))
            {
                palabras[i] = diccionario[palabra];
            }
            else if (diccionario.ContainsValue(palabra))
            {
                foreach (var item in diccionario)
                {
                    if (item.Value == palabra)
                    {
                        palabras[i] = item.Key;
                        break;
                    }
                }
            }
        }

        Console.WriteLine("\nSu frase traducida es: " + string.Join(" ", palabras));
    }

    static void AgregarPalabra()
    {
        Console.Write("\nIngrese la palabra en inglés: ");
        string ingles = Console.ReadLine().ToLower();
        Console.Write("Ingrese la traducción en español: ");
        string español = Console.ReadLine().ToLower();

        if (!diccionario.ContainsKey(ingles))
        {
            diccionario.Add(ingles, español);
            Console.WriteLine("Palabra agregada correctamente.");
        }
        else
        {
            Console.WriteLine("La palabra ya existe en el diccionario.");
        }
    }
}
