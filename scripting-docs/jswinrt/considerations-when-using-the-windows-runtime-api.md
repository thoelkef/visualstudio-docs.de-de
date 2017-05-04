---
title: "&#220;berlegungen zur Verwendung der Windows-Runtime-API | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows-Runtime-API"
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# &#220;berlegungen zur Verwendung der Windows-Runtime-API
Sie können fast jedes Element der Windows\-Runtime\-API in JavaScript verwenden.  Es gibt jedoch einige Aspekte der JavaScript\-Darstellung der Windows\-Runtime\-Elemente, die Sie beachten sollten.  
  
> [!IMPORTANT]
>  Informationen zum Erstellen von Windows\-Runtime\-Komponenten in C\+\+, C\# oder Visual Basic und deren Verwendung in JavaScript finden Sie unter [Erstellen von Windows\-Runtime\-Komponenten](http://msdn.microsoft.com/library/9a6b8f0a-7d5e-40a0-a9c5-a59b4908e133).  
  
## Sonderfälle in der JavaScript\-Darstellung von Windows\-Runtime\-Typen  
  
-   Zeichenfolgen: Eine nicht initialisierte Zeichenfolge wird als die Zeichenfolge "undefined" und eine auf `null` festgelegte Zeichenfolge wird als die Zeichenfolge "NULL" an eine Windows\-Runtime\-Methode übergeben. \(Dies gilt, wenn ein `null`\- oder `undefined`\-Wert in eine Zeichenfolge umgewandelt wird.\) Bevor Sie eine Zeichenfolge an eine Windows Runtime\-Methode übergeben, sollten Sie diese als die leere Zeichenfolge \(""\) initialisieren.  
  
-   Schnittstellen: Eine Windows\-Runtime\-Schnittstelle kann nicht in JavaScript implementiert werden.  
  
-   Arrays: Windows\-Runtime\-Arrays können nicht in der Größe geändert werden, sodass Methoden zum Ändern der Größe von Arrays in JavaScript in Windows\-Runtime\-Arrays nicht funktionieren.  
  
-   Arrays: Wenn Sie einen JavaScript\-Arraywert an eine Windows\-Runtime\-Methode übergeben, wird das Array kopiert.  Die Windows\-Runtime\-Methode kann weder das Array noch dessen Member ändern und es an die JavaScript\-App zurückzugeben.  Sie können jedoch typisierte Arrays verwenden \(beispielsweise, [Int32Array\-Objekt](../javascript/reference/int32array-object.md)\), die nicht kopiert werden.  
  
-   Strukturen: Windows Runtime\-Strukturen sind Objekte in JavaScript.  Wenn Sie eine Windows\-Runtime\-Struktur an eine Windows Runtime\-Methode übergeben möchten, instanziieren Sie die Struktur nicht mit dem `new`\-Schlüsselwort.  Erstellen Sie stattdessen ein Objekt, und fügen Sie die relevanten Member und deren Werte hinzu.  Die Namen der Member sollten die Camel\-Case\-Schreibweise aufweisen: `SomeStruct.firstMember`.  
  
-   Objekte: JavaScript\-Objekte sind nicht mit verwalteten Codeobjekten identisch\(`System.Object`\).  Ein JavaScript\-Objekt kann nicht an eine Windows Runtime\-Methode übergeben werden, die `System.Object` erfordert.  
  
-   Objektidentität: In den meisten Fällen ändern sich die Objekte, die zwischen Windows\-Runtime und JavaScript hin\- und herübergeben werden, nicht.  Das JavaScript\-Modul verwaltet eine Zuordnung von bekannten Objekten.  Wenn ein Objekt von Runtime\-Windows zurückgegeben wird, wird es mit der Zuordnung verglichen, und wenn es nicht vorhanden ist, wird ein neues Objekt erstellt.  Dieselbe Prozedur wird für Objekte eingehalten, die Schnittstellen darstellen, die von Windows Runtime\-Methoden zurückgegeben werden.  Es gibt zwei Arten von Ausnahmen:  
  
    -   Objekte, die von einem Windows\-Runtime\-Aufruf zurückgegeben, und denen dann neue \(expando\) Eigenschaften hinzugefügt werden, behalten ihre neuen Eigenschaften nicht bei, wenn sie zurück an Windows\-Runtime übergeben werden.  Wenn sie jedoch an die JavaScript\-App zurückgegeben werden, da sie an das vorhandene Objekt angepasst werden, weist das zurückgegebene Objekt die expando\-Eigenschaften auf.  
  
    -   Strukturen und Delegaten in Windows\-Runtime können nicht als identisch mit zuvor verwendeten Strukturen oder Delegaten identifiziert werden.  Jedes Mal, wenn eine Struktur oder ein Delegat zurückgegeben wird, erhält sie\/es einen neuen Verweis.  
  
-   Namenskonflikte: Mehrere Windows\-Runtime\-Schnittstellen haben möglicherweise Member mit den gleichen Namen.  Wenn sie in einem einzelnen JavaScript\-Objekt kombiniert werden \(das eine Darstellung einer Laufzeitklasse oder Schnittstelle sein kann\), werden die Member mit vollqualifizierten Namen dargestellt.  Sie können diese Member aufrufen, indem Sie die folgende Syntax verwenden: `Class["MemberName"](parameter)`.  
  
     Im folgenden Code weisen zwei Schnittstellen eine Draw\-Methode auf und eine Laufzeitklasse implementiert beide Schnittstellen.  
  
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
  
     Im Folgenden wird gezeigt, wie Sie den obigen Code in JavaScript aufrufen können.  
  
    ```javascript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   `Out`\-Parameter: Wenn eine Windows\-Runtime\-Methode mehrere `out`\-Parameter aufweist, verfügt die Methode in JavaScript über ein JavaScript\-Objekt als Rückgabewert, und das Objekt verfügt über Eigenschaften, die dem `out`\-Parameter entsprechen.  Betrachten Sie beispielsweise die folgende Windows\-Runtime\-Signatur in C\+\+.  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     Die JavaScript\-Version dieser Signatur ist:  
  
    ```javascript  
    var returnValue = exampleMethod();  
  
    ```  
  
     In diesem Beispiel ist `returnValue` ein JavaScript\-Objekt mit zwei Feldern: `first` und `second`.  
  
-   Statische Member: Windows\-Runtime definiert statische Member und Instanzmember.  In JavaScript werden statische Member zum Objekt hinzugefügt, das der Windows\-Runtime\-Klasse bzw. \-Schnittstelle zugeordnet ist.  
  
    ```javascript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Weitere Informationen zur JavaScript\-Darstellung von grundlegenden Windows\-Runtime\-Typen finden Sie unter [JavaScript\-Darstellung von Windows\-Runtime\-Typen](../jswinrt/javascript-representation-of-windows-runtime-types.md).