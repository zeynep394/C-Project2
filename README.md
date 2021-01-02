# Cs-Project2

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Collections;

namespace Proje2
{
    class müşteriSınıfı
    {
        public String ad;
        public int ürünSay;
        public müşteriSınıfı(String ad, int ürünSay) //constructor methodumuzu tanımlıyoruz
        {
            this.ad = ad;
            this.ürünSay = ürünSay;
        }

    }
    class Program
    {
        static String[] MüşteriAdı = { "Ali", "Merve", "Veli", "Gülay", "Okan", "Zekiye", "Kemal", "Banu", "İlker", "Songül", "Nuri", "Deniz" };

        static int[] ÜrünSayısı = { 8, 11, 16, 5, 15, 14, 19, 3, 18, 17, 13, 15 };

        static Random random = new Random(); //arraylistlerin uzunluklarını belirleyen random sayıları atamak için random objesi oluşturduk.

        public static ArrayList arrayListOluştur(String[] MüşteriAdı, int[] ÜrünSayısı,Random random)
        {
            int sayac = 0;
            int eleman = 0;
            
            ArrayList arrayList = new ArrayList(); //eleman sayısını bilmediğimiz zaman arraylist kullanabiliriz. 1 taane array list oluşturmak istediğimiz için loopun dışında tanımladık
            
            while (sayac < MüşteriAdı.Length)//random numaralrı göz önünde bulundurarak generic listeye nesne elemanları atayan while loop
            {
                int listeBoyutu = random.Next(1,6); //creates a number between 1 and 5
                List<müşteriSınıfı> liste = new List<müşteriSınıfı>(); //müşteriSınıfı tipindeki generic listesini oluşturduk.
                Console.WriteLine(listeBoyutu);
                if((MüşteriAdı.Length-sayac) < listeBoyutu)
                {
                    for(int i=0; i< MüşteriAdı.Length - sayac; i++)
                    {
                        müşteriSınıfı nesne = new müşteriSınıfı(MüşteriAdı[eleman], ÜrünSayısı[eleman]);
                        liste.Add(nesne);
                        eleman++;
                        //sayac++;
                    }
                    sayac += MüşteriAdı.Length - sayac;
                }
                else { 
                    for(int i=0; i <listeBoyutu;i++)
                    {
                        müşteriSınıfı nesne = new müşteriSınıfı(MüşteriAdı[eleman], ÜrünSayısı[eleman]);
                        liste.Add(nesne);
                        eleman++;
                        sayac++;
                    }
                }
                arrayList.Add(liste);
                


            }
            return arrayList;
        }
        static void Main(string[] args)
        {
            //String[] MüşteriAdı = { "Ali", "Merve", "Veli", "Gülay", "Okan", "Zekiye", "Kemal", "Banu", "İlker", "Songül", "Nuri", "Deniz" };

            //int[] ÜrünSayısı = { 8, 11, 16, 5, 15, 14, 19, 3, 18, 17, 13, 15 };
            int elemanSay = 0;
            ArrayList arrayList = arrayListOluştur(MüşteriAdı, ÜrünSayısı, random);
            foreach (List<müşteriSınıfı> item in arrayList)
            {
                foreach (müşteriSınıfı item1 in item)
                {
                    Console.WriteLine("{0}, {1}", item1.ad, item1.ürünSay);
                }
                Console.WriteLine();
                elemanSay++;
            }
            int listeOrt = 12 / elemanSay;
            Console.WriteLine("Dinamik Dizinin eleman sayısı: ");
            Console.WriteLine(elemanSay);
            Console.WriteLine("Listelerin ortalama eleman sayısı: ");
            Console.WriteLine(listeOrt);
            Console.ReadKey();
        }
    }
}
