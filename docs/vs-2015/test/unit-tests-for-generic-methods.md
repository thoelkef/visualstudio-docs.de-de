---
title: Komponententests für generische Methoden | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.assetid: ffc89814-a7df-44fc-aef5-dd3dfeb28a9b
caps.latest.revision: 49
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1b419568490e41b135c2c7c801154f6550c546e9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771464"
---
# <a name="unit-tests-for-generic-methods"></a>Komponententests für generische Methoden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Generieren von Komponententests für generische Methoden genau wie bei anderen Methoden, wie in beschrieben [Vorgehensweise: Erstellen und Ausführen eines Komponententests](http://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48). Die folgenden Abschnitte enthalten Informationen und Beispiele zum Erstellen von Komponententests für generische Methoden.  
  
## <a name="type-arguments-and-type-constraints"></a>Typargumente und Typeinschränkungen  
 Wenn [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] einen Komponententest für eine generische Klasse generiert, z. B. `MyList<T>`, werden zwei Methoden generiert: eine generische Hilfsmethode und eine Testmethode. Wenn `MyList<T>` über eine oder mehrere Typeinschränkungen verfügt, muss das Typargument alle Typeinschränkungen erfüllen. Um sicherzustellen, dass der zu testende generische Code bei allen zulässigen Eingaben erwartungsgemäß funktioniert, ruft die Testmethode die generische Hilfsmethode mit allen zu testenden Einschränkungen auf.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen werden Komponententests für Generics veranschaulicht:  
  
-   [Bearbeiten von generiertem Testcode](#EditingGeneratedTestCode). Dieses Beispiel besteht aus zwei Abschnitten, „Generierter Testcode“ und „Bearbeiteter Testcode“. Es veranschaulicht, wie der von einer generischen Methode generierte Rohdaten-Testcode bearbeitet wird, um eine hilfreiche Testmethode zu erhalten.  
  
-   [Verwenden einer Typeinschränkung](#TypeConstraintNotSatisfied). In diesem Beispiel wird ein Komponententest für eine generische Methode veranschaulicht, die eine Typeinschränkung verwendet. Die Typeinschränkung wird in diesem Beispiel nicht erfüllt.  
  
###  <a name="EditingGeneratedTestCode"></a> Beispiel 1: Bearbeiten von generiertem Testcode  
 Im Testcode in diesem Abschnitt wird eine Code-unter-Test-Methode mit dem Namen `SizeOfLinkedList()` getestet. Diese Methode gibt eine ganze Zahl zurück, die die Anzahl der Knoten in der verknüpften Liste angibt.  
  
 Das erste Codebeispiel im Abschnitt „Generierter Testcode“ enthält den unbearbeiteten Testcode, wie er von Visual Studio Enterprise generiert wurde. Das zweite Beispiel im Abschnitt „Bearbeiteter Testcode“ veranschaulicht, wie Sie die Funktionsweise der SizeOfLinkedList-Methode für zwei verschiedene Datentypen, `int` und `char`, testen können.  
  
 Dieser Code zeigt zwei Methoden:  
  
-   eine Testhilfsmethode, `SizeOfLinkedListTestHelper<T>()`. Der Name einer Testhilfsmethode enthält standardmäßig den Begriff „TestHelper“.  
  
-   eine Testmethode, `SizeOfLinkedListTest()`. Jede Testmethode wird mit dem TestMethod-Attribut markiert.  
  
#### <a name="generated-test-code"></a>Generierter Testcode  
 Der folgende Testcode wurde von der `SizeOfLinkedList()`-Methode generiert. Da es sich um den unbearbeiteten, generierten Test handelt, muss er geändert werden, damit die SizeOfLinkedList-Methode ordnungsgemäß getestet wird.  
  
```  
public void SizeOfLinkedListTestHelper<T>()  
{  
    T val = default(T); // TODO: Initialize to an appropriate value  
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value  
    int expected = 0; // TODO: Initialize to an appropriate value  
    int actual;  
    actual = target.SizeOfLinkedList();  
    Assert.AreEqual(expected, actual);  
    Assert.Inconclusive("Verify the correctness of this test method.");  
}  
  
[TestMethod()]  
public void SizeOfLinkedListTest()  
{  
   SizeOfLinkedListTestHelper<GenericParameterHelper>();  
}  
```  
  
 Im vorangehenden Code ist der generische Typparameter `GenericParameterHelper`. Obwohl er zur Angabe bestimmter Datentypen geändert werden kann, wie aus dem folgenden Beispiel ersichtlich, könnten Sie den Test ausführen, ohne diese Anweisung zu bearbeiten.  
  
#### <a name="edited-test-code"></a>Bearbeiteter Testcode  
 Im folgenden Code wurden die Testmethode und die Testhilfsmethode bearbeitet, damit die Code-unter-Test-Methode `SizeOfLinkedList()` erfolgreich von den Methoden getestet werden kann.  
  
##### <a name="test-helper-method"></a>Testhilfsmethode  
 Die Testhilfsmethode führt die folgenden Schritte aus, die im Code den mit Schritt 1 bis 5 beschrifteten Zeilen entsprechen.  
  
1.  Erstellen einer generischen verknüpften Liste.  
  
2.  Anfügen von vier Knoten an die verknüpfte Liste. Der Datentyp des Inhalts dieser Knoten ist unbekannt.  
  
3.  Zuweisen der erwarteten Größe der verknüpften Liste zur Variablen `expected`.  
  
4.  Berechnen der tatsächliche Größe der verknüpften Liste und Zuweisen zur Variablen `actual`.  
  
5.  Vergleichen von `actual` mit `expected` in einer Assert-Anweisung. Wenn die tatsächliche nicht der erwarteten Größe entspricht, ist der Test nicht erfolgreich.  
  
##### <a name="test-method"></a>Testmethode  
 Die Testmethode wird in den Code kompiliert, der aufgerufen wird, wenn Sie den Test SizeOfLinkedListTest ausführen. Sie führt die folgenden Schritte aus, die im Code den mit Schritt 6 bis 7 beschrifteten Zeilen entsprechen.  
  
1.  Festlegen von `<int>` beim Aufrufen der Testhilfsmethode, um sicherzustellen, dass der Test für `integer`-Variablen verwendet werden kann.  
  
2.  Festlegen von `<char>` beim Aufrufen der Testhilfsmethode, um sicherzustellen, dass der Test für `char`-Variablen verwendet werden kann.  
  
```  
  
public void SizeOfLinkedListTestHelper<T>()  
{  
    T val = default(T);   
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1  
    for (int i = 0; i < 4; i++) // step 2  
    {  
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);  
        target.Append(newNode);  
    }  
    int expected = 5; // step 3  
    int actual;  
    actual = target.SizeOfLinkedList(); // step 4  
    Assert.AreEqual(expected, actual); // step 5  
}  
  
[TestMethod()]  
public void SizeOfLinkedListTest()   
{  
    SizeOfLinkedListTestHelper<int>();  // step 6  
    SizeOfLinkedListTestHelper<char>(); // step 7  
}  
```  
  
> [!NOTE]
>  Bei jeder Ausführung des SizeOfLinkedListTest-Tests wird dessen TestHelper-Methode zweimal aufgerufen. Die Assert-Anweisung muss jedes Mal „true“ ergeben, damit der Test erfolgreich verläuft. Wenn der Test fehlschlägt, ist möglicherweise nicht klar, ob der Fehler durch den Aufruf verursacht wurde, mit dem `<int>` angegeben wurde, oder durch den Aufruf, mit dem `<char>` angegeben wurde. Um dies herauszufinden, könnten Sie die Aufrufliste überprüfen oder Haltepunkte in der Testmethode festlegen und den Test während der Ausführung debuggen. Weitere Informationen finden Sie unter [Gewusst wie: Debuggen beim Ausführen eines Tests in einer ASP.NET-Projektmappe](http://msdn.microsoft.com/library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b).  
  
###  <a name="TypeConstraintNotSatisfied"></a> Beispiel 2: Verwenden einer Typeinschränkung  
 In diesem Beispiel wird ein Komponententest für eine generische Methode veranschaulicht, die eine Typeinschränkung verwendet, die nicht erfüllt wird. Der erste Abschnitt enthält Code aus dem Code-unter-Test-Projekt. Die Typeinschränkung ist hervorgehoben.  
  
 Der zweite Abschnitt enthält Code aus dem Testprojekt.  
  
#### <a name="code-under-test-project"></a>Code-unter-Test-Projekt  
  
```  
using System;  
using System.Linq;  
using System.Collections.Generic;  
using System.Text;  
  
namespace ClassLibrary2  
{  
    public class Employee  
    {  
        public Employee(string s, int i)  
        {  
        }  
    }  
  
    public class GenericList<T> where T : Employee  
    {  
        private class Node  
        {  
            private T data;  
            public T Data  
            {  
                get { return data; }  
                set { data = value; }  
            }  
        }  
    }  
}  
```  
  
#### <a name="test-project"></a>Testprojekt  
 Wie bei allen neu generierten Komponententests müssen Sie diesem Komponententest nicht-eindeutige Assert-Anweisungen hinzufügen, damit er brauchbare Ergebnisse zurückgibt. Die Anweisungen werden nicht der mit dem TestMethod-Attribut markierten Methode hinzugefügt, sondern der TestHelper-Methode, die in diesem Test den Namen `DataTestHelper<T>()` hat.  
  
 In diesem Beispiel verfügt der generische Typparameter `T` über die Einschränkung `where T : Employee`. Diese Einschränkung wird in der Testmethode nicht erfüllt. Aus diesem Grund enthält die `DataTest()`-Methode eine Assert-Anweisung, die Sie darauf hinweist, dass die für `T` festgelegte Typeinschränkung bereitgestellt werden muss. Die Nachricht der Assert-Anweisung lautet wie folgt: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`  
  
 Anders ausgedrückt bedeutet dies: Wenn Sie die `DataTestHelper<T>()`-Methode aus der Testmethode `DataTest()` aufrufen, müssen Sie einen Parameter des Typs `Employee` oder eine von `Employee` abgeleitete Klasse übergeben.  
  
 `using ClassLibrary2;`  
  
 `using Microsoft.VisualStudio.TestTools.UnitTesting;`  
  
 `namespace TestProject1`  
  
```  
{  
    [TestClass()]  
    public class GenericList_NodeTest  
    {  
  
        public void DataTestHelper<T>()  
            where T : Employee  
        {  
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value  
            T expected = default(T); // TODO: Initialize to an appropriate value  
            T actual;  
            target.Data = expected;  
            actual = target.Data;  
            Assert.AreEqual(expected, actual);  
            Assert.Inconclusive("Verify the correctness of this test method.");  
        }  
  
        [TestMethod()]  
        public void DataTest()  
        {  
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +  
            "Please call DataTestHelper<T>() with appropriate type parameters.");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Aufbau eines Komponententests](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)   
 [Komponententest für Code](../test/unit-test-your-code.md)
