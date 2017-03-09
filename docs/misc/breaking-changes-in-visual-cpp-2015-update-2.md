---
title: "Wichtige &#196;nderungen in Visual C++ 2015 Update 2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5545ce3f-d8da-4007-88b7-8dba7dcd4d10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mithom"
---
# Wichtige &#196;nderungen in Visual C++ 2015 Update 2
Wenn Sie ein Upgrade auf Visual C\+\+ 2015 Update 2 CTP durchführen, treten unter Umständen Kompilierungs\- und\/oder Laufzeitfehler in Code auf, der zuvor ordnungsgemäß kompiliert und ausgeführt wurde. Änderungen beim Compiler oder Laufzeitverhalten, die solche Probleme verursachen, werden als *wichtige Änderungen* bezeichnet und werden in der Regel durch Änderungen im C\+\+\-Sprachstandard, in den Funktionssignaturen oder im Layout von Objekten im Arbeitsspeicher erforderlich.  
  
 Der restliche Artikel beschreibt spezifische wichtige Änderungen in Visual C\+\+ 2015 Update 2 CTP, und die Begriffe „neues Verhalten“ und „jetzt“ in diesem Artikel beziehen sich auf diese Version. Die Begriffe „altes Verhalten“ und „früher“ beziehen sich auf Visual C\+\+ 2015 Update 1 und frühere Versionen. Informationen über wichtige Änderungen, die zwischen der ersten Version von Visual C\+\+ 2015 und Visual C\+\+ 2015 Update 1 vorgenommen wurden, finden Sie unter [Wichtige Änderungen in Update 1](../misc/breaking-changes-in-visual-cpp-2015-update-1.md). Informationen zu wichtigen Änderungen, die zwischen Visual C\+\+ 2013 und Visual C\+\+ 2015 vorgenommen wurden, finden Sie unter [Wichtige Änderungen in Visual C\+\+ 2015](/visual-cpp/porting/visual-cpp-change-history-2003-20151).  
  
-   [Wichtige Compileränderungen](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Visual C\+\+\-Compiler  
  
-   **Zusätzliche Warnungen und Fehler können als Ergebnis der Teilunterstützung für den Ausdruck SFINAE ausgegeben werden.**  
  
     In früheren Versionen des Compilers werden bestimmte Arten von Ausdrücken in `decltype`\-Spezifizierern nicht analysiert, weil der Ausdruck SFINAE nicht unterstützt wird. Dieses alte Verhalten war falsch und entsprach nicht dem C\+\+\-Standard. Der Compiler analysiert diese Ausdrücke jetzt und hat aufgrund kontinuierlicher Konformitätsverbesserungen eine Teilunterstützung für den Ausdruck SFINAE. Daher gibt der Compiler jetzt Warnungen und Fehler aus, die er in Ausdrücken findet, die von früheren Versionen des Compilers nicht analysiert werden.  
  
     Wenn wegen dieses neuen Verhaltens ein `decltype`\-Ausdruck analysiert wird, der einen Typ enthält, der noch nicht deklariert ist, gibt der Compiler den Compilerfehler C2039 aus.  
  
 **Fehler C2039: *"Typ"*: Ist kein Element von *"globaler Namespace"'***     Beispiel 1: Verwendung eines nicht deklarierten Typs \(vorher\)  
  
    ```cpp  
    struct s1  
    {  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  // error C2039  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     Beispiel 1 \(nachher\)  
  
    ```cpp  
    struct s1  
    {  
      template <typename>  // forward declare s2struct s2;  
  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     Wenn wegen dieses neuen Verhaltens ein `decltype`\-Ausdruck analysiert wird, in dem das erforderliche Schlüsselwort `typename` für die Angabe fehlt, dass ein abhängiger Name ein Typ ist, gibt der Compiler die Compilerwarnung C4346 zusammen mit dem Compilerfehler C2923 aus.  
  
 **Warnung C4346: *"S2\<T\>::Typ"*: Abhängiger Name ist kein Typ Fehler C2923: *"s1"*: *"S2\<T\>::Typ"* ist kein gültiges Vorlage\-Typargument für den *T*\-Parameter**     Beispiel 2: Abhängiger Name ist kein Typ \(vorher\)  
  
    ```cpp  
    template <typename T>  
    struct s1  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    struct s2  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923  
    };  
    ```  
  
     Beispiel 2 \(nachher\)  
  
    ```cpp  
    template <typename T> struct s1 {...};  // as above  
    template <typename T> struct s2 {...};  // as above  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));  
    };  
    ```  
  
-   `volatile`  **Membervariablen verhindern implizit definierte Konstruktoren und Zuweisungsoperatoren**  
  
     In früheren Versionen des Compilers ist es für eine Klasse, die `volatile` Membervariablen hat, zulässig, dass Kopier\-\/Verschiebe\-Standardkonstruktoren und Kopier\-\/Verschiebe\-Standardzuweisungsoperatoren automatisch generiert werden. Dieses alte Verhalten war falsch und entsprach nicht dem C\+\+\-Standard. Der Compiler geht bei einer Klasse mit volatilen Membervariablen davon aus, dass sie nicht triviale Konstruktions\- und Zuweisungsoperatoren hat. Dies verhindert, dass Standardimplementierungen dieser Operatoren automatisch generiert werden.  Ist eine solche Klasse ein Member einer Union \(oder einer anonymen Union innerhalb einer Klasse\), werden Kopier\-\/Verschiebekonstruktoren und Kopier\-\/Verschiebezuweisungsoperatoren der Union \(oder die Klasse, die die anonyme Union enthält\) implizit als gelöscht definiert. Wird versucht, die Union \(oder die Klasse, die die anonyme Union enthält\) zu erstellen oder zu kopieren, ohne sie explizit zu definieren, tritt ein Fehler auf, und der Compiler gibt daher den Compilerfehler C2280 aus.  
  
 **Fehler C2280: *"B::B\(const B &\)"*: Es wurde versucht, auf eine gelöschte Funktion zu verweisen**     Beispiel \(vorher\)  
  
    ```cpp  
    struct A  
    {  
      volatile int i;  
      volatile int j;  
    };  
  
    extern A* pa;  
  
    struct B  
    {  
      union  
      {  
        A a;  
        int i;  
      };  
    };  
  
    B b1 {*pa};  
    B b2 (b1);  // error C2280  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
    struct A  
    {  
      int i;int j;  
    };  
  
    extern volatile A* pa;  
  
    A getA()  // returns an A instance copied from contents of pa  
    {  
      A a;  
      a.i = pa->i;  
      a.j = pa->j;  
      return a;  
    }  
  
    struct B;  // as above  
  
    B b1 {GetA()};  
    B b2 (b1);  // error C2280  
    ```  
  
-   **Statische Memberfunktionen unterstützen keine CCV\-Qualifizierer.**  
  
     In früheren Versionen von Visual C\+\+ 2015 ist es zulässig, dass statische Memberfunktionen CV\-Qualifizierer haben. Dieses Verhalten ist durch einen Rückschritt in Visual C\+\+ 2015 und Visual C\+\+ 2015 Update 1 begründet. Visual C\+\+ 2013 und frühere Versionen von Visual C\+\+ weisen Code zurück, der in dieser Weise geschrieben ist. Das Verhalten von Visual C\+\+ 2015 und Visual C\+\+ 2015 Update 1 ist falsch und entspricht nicht dem C\+\+\-Standard.  Visual Studio 2015 Update 2 weist Code, der in dieser Weise geschrieben ist, zurück und gibt stattdessen den Compilerfehler C2511 aus.  
  
 **Fehler C2511: "void A::func\(void\) const": Überladene Memberfunktion nicht in "A" gefunden**     Beispiel \(vorher\)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     Beispiel \(nachher\)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **Vorwärtsdeklaration einer Enumeration ist in WinRT\-Code nicht zulässig** \(betrifft nur \/Zw\)  
  
     In Code, der für Windows\-Runtime \(WinRT\) kompiliert wird, darf es keine Vorwärtsdeklarationen von `enum`\-Typen geben. Dies ist ähnlich zu dem Fall, dass verwalteter C\+\+\-Code für .NET Framework mit dem Compilerschalter \/clr kompiliert wird. Dieses Verhalten stellt sicher, dass die Größe einer Enumeration immer bekannt ist und richtig in das WinRT\-Typsystem projiziert werden kann. Der Compiler lehnt in dieser Weise geschriebenen Code ab und gibt den Compilerfehler C2599 zusammen mit dem Compilerfehler C3197 aus.  
  
 **Fehler C2599: *"BenutzerdefEnum"*: Die Vorwärtsdeklaration einer WinRT\-Enumeration ist nicht zulässig. Fehler C3197: *"public"*: kann nur in Definitionen verwendet werden.**     Beispiel \(vorher\)  
  
    ```cpp  
    namespace A {  
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197  
    }  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
  
              // forward declaration of CustomEnum removed  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
-   **new\- oder delete\-Funktionen eines überladenen Nicht\-Memberoperators dürfen nicht inline deklariert werden** \(Level 1 \(\/W1\) standardmäßig aktiviert\)  
  
     Frühere Versionen des Compilers geben keine Warnung aus, wenn new\- oder delete\-Funktionen eines Nicht\-Memberoperators inline deklariert werden. In dieser Weise geschriebener Code ist nicht wohlgeformt \(keine Diagnose erforderlich\) und kann zu Arbeitsspeicherproblemen führen, die sich aus nicht zusammengehörigen new\- und delete\-Operatoren ergeben \(insbesondere bei Verwendung von Zuordnungsaufhebung mit Größenangabe\), die sich nur schwer diagnostizieren lassen.   Der Compiler gibt jetzt die Warnung C4595 aus, um Code erkennen zu können, der in dieser Weise geschrieben ist.  
  
 **Warnung C4595: *"operator new"*: Die new\- oder delete\-Funktionen eines Nicht\-Memberoperators dürfen nicht inline deklariert werden.**     Beispiel \(vorher\)  
  
    ```cpp  
  
              inline void* operator new(size_t sz)  // warning C4595  
    {  
      ...  
    }  
    ```  
  
     Beispiel \(nachher\)  
  
    ```cpp  
  
              void* operator new(size_t sz)  // removed inline  
    {  
      ...  
    }  
    ```  
  
     Ein Korrigieren von Code, der in dieser Weise geschrieben ist, kann erfordern, dass die Operatordefinitionen aus einer Headerdatei in eine entsprechende Quelldatei verschoben werden.