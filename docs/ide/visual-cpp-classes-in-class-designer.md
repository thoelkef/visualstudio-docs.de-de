---
title: "Visual C++ Classes in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritancelinelabel"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], classes"
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Classes in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vom Klassen\-Designer werden C\+\+\-Klassen unterstützt und systemeigene C\+\+\-Klassen auf die gleiche Weise wie Visual Basic\- oder Visual C\#\-Klassenformen grafisch dargestellt, mit der Ausnahme, dass C\+\+\-Klassen mehrere Vererbungsbeziehungen aufweisen können.  Sie können die Klassenform erweitern, um weitere Felder und Methoden in der Klasse anzuzeigen, oder die Klassenform reduzieren, um Platz zu sparen.  
  
> [!NOTE]
>  Vom Klassen\-Designer werden keine Unions unterstützt \(ein spezieller Klassentyp, in dem der belegte Speicherplatz nur so groß wie der größte Datenmember der Union ist\).  
  
## Einfache Vererbung  
 Wenn Sie mehrere Klassen mit einer Vererbungsbeziehung in ein Klassendiagramm ziehen, sind diese durch einen Pfeil verbunden.  Der Pfeil zeigt in die Richtung der Basisklasse.  Wenn beispielsweise die folgenden Klassen in einem Klassendiagramm angezeigt werden, sind sie durch einen Pfeil von B nach A verbunden:  
  
```  
class A {};  
class B : A {};  
```  
  
 Sie können auch nur Klasse B in das Klassendiagramm ziehen, mit der rechten Maustaste auf die Klassenform für B klicken und anschließend auf **Basisklassen anzeigen** klicken.  Hierdurch wird ihre Basisklasse angezeigt: A.  
  
## Mehrfachvererbung  
 Der Klassen\-Designer unterstützt die Visualisierung von Vererbungsbeziehungen für mehrere Klassen.  *Mehrfachvererbung* wird verwendet, wenn eine abgeleitete Klasse Attribute von mehreren Basisklassen enthält.  Folgendes ist ein Beispiel für Mehrfachvererbung:  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 Wenn Sie mehrere Klassen mit einer Vererbungsbeziehung in das Klassendiagramm ziehen, sind diese durch einen Pfeil verbunden.  Der Pfeil zeigt in Richtung der Basisklassen.  
  
 Wenn Sie mit der rechten Maustaste auf eine Klassenform und anschließend auf **Basisklassen anzeigen** klicken, werden die Basisklassen für die ausgewählte Klasse angezeigt.  
  
> [!NOTE]
>  Der Befehl **Abgeleitete Klassen anzeigen** wird für C\+\+\-Code nicht unterstützt.  Sie können abgeleitete Klassen anzeigen, indem Sie zur Klassenansicht wechseln, den Typknoten und den Unterordner **Abgeleitete Typen** erweitern und diese Typen dann in das Klassendiagramm ziehen.  
  
 Weitere Informationen zu Mehrfachvererbung finden Sie unter [\(NOTINBUILD\) Multiple Inheritance](http://msdn.microsoft.com/de-de/3b74185e-2beb-4e29-8684-441e51d2a2ca) und unter [Mehrere Basisklassen](/visual-cpp/cpp/multiple-base-classes).  
  
## Abstrakte Klassen  
 Der Klassen\-Designer unterstützt abstrakte Klassen \(auch als "abstrakte Basisklassen" bezeichnet\).  Dies sind Klassen, die nicht instanziiert werden, von denen jedoch andere Klassen abgeleitet werden können.  Unter Verwendung eines Beispiels aus "Mehrfachvererbung" weiter oben in diesem Dokument können Sie die `Bird`\-Klasse als einzelne Objekte wie folgt instanziieren:  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 Es ist jedoch nicht möglich, die `Swimmer`\-Klasse als einzelne Objekte zu instanziieren.  Sie können davon nur andere Tierklassentypen ableiten, beispielsweise `Penguin`, `Whale` und `Fish`.  In diesem Fall würde die `Swimmer`\-Klasse als abstrakte Basisklasse deklariert werden.  
  
 Eine Klasse kann mit dem `abstract`\-Schlüsselwort als abstrakt deklariert werden.  Member, die als abstrakt gekennzeichnet oder in einer abstrakten Klasse enthalten sind, sind virtuell und müssen von Klassen implementiert werden, die von der abstrakten Klasse abgeleitet sind.  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 Eine Klasse kann auch als abstrakt deklariert werden, indem mindestens eine rein virtuelle Funktion eingeschlossen wird:  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 Wenn diese Deklarationen in einem Klassendiagramm angezeigt werden, wird der Klassenname `Swimmer` und dessen rein virtuelle Funktion `swim` kursiv in Form einer abstrakten Klassen zusammen mit der Bezeichnung **Abstrakte Klasse** angezeigt.  Beachten Sie, dass die Typform der abstrakten Klasse die einer normalen Klasse ist, außer dass der Rahmen eine gepunktete Linie ist.  
  
 Eine Klasse, die von der abstrakten Basisklasse abgeleitet ist, muss jede rein virtuelle Funktion in der Basisklasse überschreiben, andernfalls kann die abgeleitete Klasse nicht instanziiert werden.  Wenn beispielsweise eine `Fish`\-Klasse von der `Swimmer`\-Klasse abgeleitet wird, muss `Fish` die `swim`\-Methode überschreiben:  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 Wenn dieser Code in einem Klassendiagramm angezeigt wird, zeichnet der Klassen\-Designer eine Vererbungslinie von `Fish` zu `Swimmer`.  
  
## Anonyme Klassen  
 Der Klassen\-Designer unterstützt anonyme Klassen.  *Anonyme Klassentypen* sind Klassen, die ohne Bezeichner deklariert werden.  Sie können keinen Konstruktor oder Destruktor enthalten und weder als Argumente an Funktionen übergeben noch als Rückgabewerte von Funktionen zurückgegeben werden.  Sie können eine anonyme Klasse verwenden, um einen Klassennamen durch den Namen einer Typdefinition \(typedef\) zu ersetzen, wie in dem folgenden Beispiel:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 Auch Strukturen können anonym sein.  Vom Klassen\-Designer werden anonyme Klassen angezeigt und auf die gleiche Weise wie der jeweilige Typ strukturiert.  Der von Ihnen festgelegte Tagname wird vom Klassen\-Designer nicht verwendet, obwohl Sie anonyme Klassen und Strukturen deklarieren und anzeigen können.  Der Name wird verwendet, der von der Klassenansicht generiert wird.  Die Klasse bzw. Struktur wird in der Klassenansicht und im Klassen\-Designer als ein Element mit der Bezeichnung **\_\_unnamed** \(unbenannt\) angezeigt.  
  
 Weitere Informationen zu anonymen Klassen finden Sie unter [Anonyme Klassentypen](/visual-cpp/cpp/anonymous-class-types).  
  
## Vorlagenklassen  
 Der Klassen\-Designer unterstützt die Visualisierung von Vorlagenklassen.  Geschachtelte Deklarationen werden unterstützt.  In der folgenden Tabelle sind einige typische Deklarationen dargestellt.  
  
|Codeelement|Ansicht Klassen\-Designer|  
|-----------------|-------------------------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Vorlagenklasse|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Vorlagenklasse|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Vorlagenklasse|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Vorlagenklasse|  
  
 In der folgenden Tabelle sind einige Beispiele für teilweise Spezialisierungen dargestellt.  
  
|Codeelement|Ansicht Klassen\-Designer|  
|-----------------|-------------------------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Vorlagenklasse|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Vorlagenklasse|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Vorlagenklasse|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Vorlagenklasse|  
  
 In der folgenden Tabelle sind einige Beispiele für Vererbungen in teilweisen Spezialisierungen dargestellt.  
  
|Codeelement|Ansicht Klassen\-Designer|  
|-----------------|-------------------------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Vorlagenklasse<br /><br /> `B`<br /><br /> Klasse<br /><br /> \(zeigt auf Klasse A\)<br /><br /> `C`<br /><br /> Klasse<br /><br /> \(zeigt auf Klasse A\)|  
  
 In der folgenden Tabelle sind einige Beispiele für Vorlagenfunktionen von teilweisen Spezialisierungen dargestellt.  
  
|Codeelement|Ansicht Klassen\-Designer|  
|-----------------|-------------------------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U\> \(\+ 1 overload\)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Vorlagenklasse<br /><br /> `B<T2>`<br /><br /> Vorlagenklasse<br /><br /> \(B ist in Klasse A unter **Geschachtelte Typen** enthalten\)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Klasse<br /><br /> \-\> C\<int\><br /><br /> `C<T>`<br /><br /> Vorlagenklasse|  
  
 In der folgenden Tabelle sind einige Beispiele für Vorlagenvererbungen dargestellt.  
  
|Codeelement|Ansicht Klassen\-Designer|  
|-----------------|-------------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Klasse<br /><br /> \-\>B<br /><br /> `C<int>`<br /><br /> Klasse<br /><br /> \(B ist in Klasse C unter **Geschachtelte Typen** enthalten\)<br /><br /> `C<T>`<br /><br /> Vorlagenklasse|  
  
 In der folgenden Tabelle sind einige Beispiele für kanonisch spezialisierte Klassenverbindungen dargestellt.  
  
|Codeelement|Ansicht Klassen\-Designer|  
|-----------------|-------------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Klasse<br /><br /> \-\>C\<int\><br /><br /> `C<int>`<br /><br /> Klasse<br /><br /> `C<T>`<br /><br /> Vorlagenklasse<br /><br /> `D`<br /><br /> Klasse<br /><br /> \-\>C\<float\>|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T\>|  
  
## Siehe auch  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Klassen und Strukturen](/visual-cpp/cpp/classes-and-structs-cpp)   
 [Anonyme Klassentypen](/visual-cpp/cpp/anonymous-class-types)   
 [\(NOTINBUILD\) Multiple Inheritance](http://msdn.microsoft.com/de-de/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [Mehrere Basisklassen](/visual-cpp/cpp/multiple-base-classes)   
 [Vorlagen](/visual-cpp/cpp/templates-cpp)