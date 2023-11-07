# odev-5
odev 5 

1) UML nedir?
   UML veya Birleşik Modelleme Dili, yazılım geliştiricilerin yeni sistemleri görselleştirmesine ve oluşturmasına yardımcı olan görsel bir modelleme dilidir. Bu bir programlama dili değil; özellikle diyagram çizmeye yönelik bir dizi kuraldır.


    En yaygın kullanılan UML nedir?
    Yazılım tipik olarak nesneye özgü programlamaya dayandığından, sınıf diyagramı muhtemelen en yaygın kullanılan UML diyagramıdır.


   İşlevleri ile yazınız.
   Gereksinimlerin titizlikle tanımlandığı, özellik kayması veya döndürme olasılığının çok düşük olduğu (gömülü kontrol sistemleri, kurumsal sözleşmeli işler vb. düşünün) bir sistem oluşturuyorsanız, UML'nin size yardımcı olacak yararlı bir araç olacağı bilinmelidir.

Belirsiz gereksinimlerin önce çözülmesi ve bunları sistemlerle eşleştirilmesi gerekir.
Çalışmanızı belgeleyin (böylece başkaları anlayabilir).
Kendinizi koruyun (paylaşmak istediklerini yapmadığınızı iddia etmesi durumunda).
Ancak günümüzde yazılım geliştirmenin büyük bir kısmı, teknik bir zorluk olduğu kadar, bir ürün zorluğudur. İnşa edene kadar ne inşa etmek istediğini bilemezsin. Ve bu durumlarda, UML diyagramları (veya diğer modeller, planlar veya tasarımlar) çöpe atılıyor.

Benim önerim, ihtiyacınız olana kadar öğrenmekten kaçınmak olacaktır. Kendinizi UML bilmenizi gerektiren işlere başvururken bulursanız UML öğrenilmelidir. 
   


    2) ArrayList, LinkedList, Hashmap ve HashSet'in farkları ve kullanım amaçları nelerdir?
    ArrayList
ArrayList, Java'daki Liste arayüzünün en yaygın kullanılan uygulamasıdır. Yerleşik dizilere dayanır ancak öğe ekledikçe veya çıkardıkça dinamik olarak büyüyüp küçülebilir.

Erişim listesi elemanlarına sıfırdan başlayan indeksler kullanıyoruz. Listenin sonuna veya belirli bir konumuna yeni bir öğe ekleyebiliriz
List<String> list = new ArrayList<>();
list.add("Daniel");
list.add(0, "Marko");
assertThat(list).hasSize(2);
assertThat(list.get(0)).isEqualTo("Marko");
Copy
To remove an element from the list, we need to provide the object reference or its index:

List<String> list = new ArrayList<>(Arrays.asList("Daniel", "Marko"));
list.remove(1);
assertThat(list).hasSize(1);
assertThat(list).doesNotContain("Marko");


 ArrayList bize Java'da dinamik diziler sağlar. Yerleşik dizilerden daha yavaş olmasına rağmen ArrayList, programlama çabasından tasarruf etmemize ve kod okunabilirliğini geliştirmemize yardımcı olur.

Zaman karmaşıklığından bahsederken Big-O notasyonunu kullanırız. Gösterim, algoritmayı gerçekleştirme süresinin girdi boyutuyla birlikte nasıl büyüdüğünü açıklar.

ArrayList, diziler indekslere dayalı olduğundan rastgele erişime izin verir. Bu, herhangi bir öğeye erişimin her zaman O(1) sabit bir zaman alması anlamına gelir.

Yeni öğelerin eklenmesi de O(1) zaman alır; ancak belirli bir konuma/indekse öğe eklenmesi veya en kötü senaryoda, yeni bir dizinin oluşturulması ve tüm öğelerin ona kopyalanması gerektiği durumlar dışında,
bu süre O alır. (N). Verilen listede belirli bir öğenin bulunup bulunmadığının kontrol edilmesi doğrusal O(n) süresinde çalışır.

Aynı şey elemanların çıkarılması için de geçerlidir. Kaldırılmak üzere seçilen öğeyi bulmak için tüm diziyi yinelememiz gerekir.

    Kullanım
Hangi koleksiyon türünü kullanacağımızdan emin olmadığımızda ArrayList ile başlamak muhtemelen iyi bir fikirdir. Dizinlere dayalı öğelere erişimin çok hızlı olacağını unutmayın. Ancak öğeleri değerlerine göre aramak veya belirli bir konuma öğe eklemek/çıkarmak pahalı olacaktır.

Öğelerin aynı sırasını korumanın önemli olduğu durumlarda ArrayList'in kullanılması anlamlıdır ve konuma/indekse dayalı hızlı erişim süresi önemli bir kriterdir.

Öğelerin sırası önemli olmadığında ArrayList'i kullanmaktan kaçının. Ayrıca öğelerin sıklıkla belirli bir konuma eklenmesi gerektiğinde bundan kaçınmaya çalışın. Benzer şekilde, özellikle liste büyükse, belirli öğe değerlerini ararken önemli bir gereklilik olduğunda ArrayList'in en iyi seçenek olmayabileceğini unutmayın.

LinkedList
Bağlantılı liste
LinkedList çift bağlantılı bir liste uygulamasıdır. Hem List hem de Deque (Queue'nun bir uzantısı) arayüzlerinin uygulanması. ArrayList'in aksine, LinkedList'te veri sakladığımızda her öğe bir öncekiyle bağlantıyı korur.

LinkedList, standart Liste ekleme yöntemlerinin yanı sıra, listenin başına veya sonuna öğe ekleyebilen ek yöntemleri de destekler:
LinkedList<String> listesi = new LinkedList<>();
list.addLast("Daniel");
list.addFirst("Marko");
iddiaBu(liste).hasSize(2);
iddiaThat(list.getLast()).isEqualTo("Daniel");
Kopyala
Bu liste uygulaması aynı zamanda listenin başındaki veya sonundaki öğelerin kaldırılmasına yönelik yöntemler de sunar:

LinkedList<String> list = new LinkedList<>(Arrays.asList("Daniel", "Marko", "David"));
list.removeFirst();
list.removeLast();
iddiaBu(liste).hasSize(1);
iddiaThat(list).containsExactly("Marko");
Kopyala
Uygulanan Deque arayüzü, elemanların alınması, eklenmesi ve silinmesi için kuyruğa benzer yöntemler sağlar:

LinkedList<String> listesi = new LinkedList<>();
list.push("Daniel");
list.push("Marko");
iddiaThat(list.poll()).isEqualTo("Marko");
iddiaBu(liste).hasSize(1);

Kullanım
Çoğu zaman ArrayList'i varsayılan Liste uygulaması olarak kullanabiliriz. Ancak bazı kullanım durumlarında LinkedList'ten faydalanmalıyız. Bunlar arasında sabit ekleme ve silme süresini, sabit erişim süresini ve etkili bellek kullanımını tercih ettiğimiz durumlar yer alır.

LinkedList'in kullanılması, aynı öğe sırasını koruduğunuzda anlamlıdır ve hızlı ekleme süresi (öğeleri herhangi bir konuma ekleme ve çıkarma) önemli bir kriterdir.

ArrayList gibi, öğelerin sırası önemli olmadığında LinkedList'i kullanmaktan kaçınmalıyız. Hızlı erişim süresi veya öğeleri aramanın önemli bir gereklilik olduğu durumlarda LinkedList en iyi seçenek değildir.

ArrayList ve LinkedList'in aksine HashMap, Harita arayüzünü uygular. Bu, her anahtarın tam olarak tek bir değerle eşlendiği anlamına gelir. Koleksiyondan karşılık gelen değeri almak için her zaman anahtarı bilmemiz gerekir.
Map<String, String> map = new HashMap<>();
map.put("123456", "Daniel");
map.put("654321", "Marko");
assertThat(map.get("654321")).isEqualTo("Marko");,
Benzer şekilde, koleksiyondan bir değeri yalnızca anahtarını kullanarak silebiliriz:
Map<String, String> map = new HashMap<>();
map.put("123456", "Daniel");
map.put("654321", "Marko");
map.remove("654321");
assertThat(map).hasSize(1);

Birisi şu soruyu sorabilir: Neden sadece bir Liste kullanıp anahtarlardan hep birlikte kurtulmuyoruz? Özellikle HashMap, anahtarları kaydetmek için daha fazla bellek tükettiğinden ve girişleri sıralanmadığından. Cevap, arama öğelerinin performans avantajlarında yatmaktadır.

HashMap, bir anahtarın var olup olmadığını kontrol etmede veya bir anahtara dayalı bir değer almada çok etkilidir. Bu işlemler ortalama O(1) alır.

Bir anahtara dayalı olarak HashMap'e öğe eklemek ve kaldırmak O(1) sabit zaman alır. Anahtarı bilmeden bir öğenin kontrol edilmesi, tüm öğelerin üzerinde döngü yapılması gerektiğinden O(n) doğrusal süresini alır.



2) Parametresi ile aldığı yazının küçük harflerini büyük harfe, büyük harflerini küçük harfe çevirip yeni bir String ile geri dönen changeCase isimli metodu yazınız.
    public class harfDegistirme {
    public static void main(String[] args) {
        String str = "SeLaM KıZlAr";
        String result = changeCase(str);
        System.out.println(result);
    }

    public static String changeCase(String str) {
        StringBuilder result = new StringBuilder();
        for (int i = 0; i < str.length(); i++) {
            char ch = str.charAt(i);
            if (Character.isUpperCase(ch)) {
                result.append(Character.toLowerCase(ch));
            } else {
                result.append(Character.toUpperCase(ch));
            }
        }
        return result.toString();
    }



3) Parametresi ile aldığı iki yazının birincisi içerisinden ikincisindeki karakterlerin silinmiş olduğu yeni bir String döndüren squeezeisimli metodu yazınız ve test ediniz
   import java.util.Scanner;

public class Squeeze {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("İki kelime giriniz: ");
        String word1 = scanner.next();
        String word2 = scanner.next();
        String result = "";
        for (int i = 0; i < word2.length(); i++) {
            char c = word2.charAt(i);
            if (word1.indexOf(c) == -1) {
                result += c;
            }
        }
        System.out.println("Sonuç: " + result);
    }
}

   































