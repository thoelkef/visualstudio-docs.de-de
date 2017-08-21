---
title: "Überlegungen zur Verwendung der Windows-Runtime-API | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime API
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: 693b3dac9def5533417638c3ec1c0de8db1d5fe3
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---
# <a name="considerations-when-using-the-windows-runtime-api"></a>Überlegungen zur Verwendung der Windows-Runtime-API
Sie können fast jedes Element der Windows-Runtime-API in JavaScript verwenden. Es gibt jedoch einige Aspekte der JavaScript-Darstellung von Windows-Runtime-Elementen, die Sie bedenken sollten.  
  
> [!IMPORTANT]
>  Informationen zum Erstellen von Windows-Runtime-Komponenten in C++, C# oder Visual Basic, die in JavaScript genutzt werden können, finden Sie unter [Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) und [Erstellen von Windows-Runtime-Komponenten in C# und Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="special-cases-in-the-javascript-representation-of-windows-runtime-types"></a>Besondere Fälle bei der JavaScript-Darstellung von Windows-Runtime-Typen  
  
-   Zeichenfolgen: Eine nicht initialisierte Zeichenfolge wird der Windows-Runtime-Methode als Zeichenfolge „undefined“ übergeben. Eine Zeichenfolge mit dem Wert `null` wird als Zeichenfolge „null“ übergeben. Dies ist immer dann der Fall, wenn der Wert `null` oder `undefined` in eine Zeichenfolge umgewandelt wird. Bevor Sie einer Windows-Runtime-Methode eine Zeichenfolge übergeben, sollten Sie sie als leere Zeichenfolge ("") initialisieren.  
  
-   Schnittstellen: Eine Windows-Runtime-Schnittstelle kann nicht in JavaScript implementiert werden.  
  
-   Arrays: Die Größe von Windows-Runtime-Arrays kann nicht geändert werden. Methoden, die in JavaScript die Größe von Arrays ändern, können daher nicht für Windows-Runtime-Arrays verwendet werden.  
  
-   Arrays: Wenn Sie einer Windows-Runtime-Methode einen JavaScript-Arraywert übergeben, wird das Array kopiert. Die Windows-Runtime-Methode kann nicht das Array oder seine Elemente ändern und das Array an die JavaScript-App zurückgeben. Allerdings können Sie typisierte Arrays (z.B. [Int32Array-Objeke](../javascript/reference/int32array-object.md)) verwenden, die nicht kopiert werden.  
  
-   Strukturen: Windows-Runtime-Strukturen sind in JavaScript Objekte. Wenn Sie eine Windows-Runtime-Struktur an eine Windows-Runtime-Methode übergeben möchten, instanziieren Sie die Struktur nicht mit dem Schlüsselwort `new`. Erstellen Sie stattdessen ein Objekt, und fügen Sie die relevanten Member und ihre Werte hinzu. Die Namen der Member sollten in Goß-/Kleinbuchstaben geschrieben werden: `SomeStruct.firstMember`.  
  
-   Objekte: JavaScript-Objekte sind nicht identisch mit verwalteten Codeobjekten (`System.Object`). Ein JavaScript-Objekt kann nicht an eine Windows-Runtime-Methode übergeben werden, die ein `System.Object` benötigt.  
  
-   Objekt-Identität: Objekte, die von der Windows-Runtime an JavaScript übergeben werden und umgekehrt, ändern sich in den meisten Fällen nicht. Das JavaScript-Modul verwaltet eine Zuordnung der bekannten Objekte. Wird ein Objekt von der Windows-Runtime zurückgegeben, wird es mit den zugeordneten Objekten abgeglichen. Wenn das Objekt nicht vorhanden ist, wird ein neues Objekt erstellt. Das Gleiche geschieht bei Objekten, die Schnittstellen darstellen und von Windows-Runtime-Methoden zurückgegeben werden. Es gibt zwei Arten von Ausnahmen:  
  
    -   Objekte, die durch einen Windows-Runtime-Aufruf zurückgegeben werden und denen anschließend neue (Expando-)Eigenschaften hinzugefügt werden, verlieren ihre Eigenschaften, sobald sie erneut der Windows-Runtime übergeben werden. Wenn die Objekte allerdings an die JavaScript-App zurückgegeben werden, verfügt das zurückgegebene Objekt über die Expando-Eigenschaften, weil die Objekte dem vorhandenen Objekt zugeordnet werden können.  
  
    -   Strukturen und Delegate in der Windows-Runtime sind nicht mit den zuvor verwendeten Strukturen und Delegaten identisch. Jedes Mal, wenn Strukturen oder Delegate zurückgegeben werden, geben sie einen neuen Verweis zurück.  
  
-   Namenskonflikte: Mehrere Windows-Runtime-Schnittstellen können über gleichnamige Member verfügen. Wenn sie in einem einzelnen JavaScript-Objekt kombiniert werden, das eine Darstellung einer Laufzeitklasse oder einer Schnittstelle sein kann, werden die Member mit vollqualifizierten Namen dargestellt. Sie können diese Member mit der folgenden Syntax aufrufen: `Class["MemberName"](parameter)`.  
  
     Im folgenden Codebeispiel verfügen zwei Schnittstellen über eine Draw-Methode. Eine Laufzeitklasse implementiert beide Schnittstellen.  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     Den oben aufgeführten Code können Sie in JavaScript folgendermaßen aufrufen:  
  
    ```JavaScript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   `Out`-Parameter: Wenn eine Windows-Runtime-Methode mehrere `out`-Parameter besitzt, gibt die Methode in JavaScript ein JavaScript-Objekt zurück. Das Objekt verfügt über Eigenschaften, die dem `out`-Parameter entsprechen. Betrachten Sie beispielsweise die folgende Windows-Runtime-Signatur in C++:  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     Die JavaScript-Version dieser Signatur sieht wie folgt aus:  
  
    ```JavaScript  
    var returnValue = exampleMethod();  
  
    ```  
  
     In diesem Beispiel ist `returnValue` ein JavaScript-Objekt, das über zwei Felder verfügt: `first` und `second`.  
  
-   Statische Member: Die Windows-Runtime definiert sowohl statische Member als auch Instanzmember. In JavaScript werden statische Member dem Objekt hinzugefügt, das der Windows-Runtime-Klasse oder -Schnittstelle zugeordnet ist.  
  
    ```JavaScript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Weitere Informationen zur JavaScript-Darstellung von Windows-Runtime-Basistypen finden Sie unter [JavaScript-Darstellung von Windows-Runtime-Typen](../jswinrt/javascript-representation-of-windows-runtime-types.md).
