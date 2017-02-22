---
title: "Working with Visual C++ Code (Class Designer) | Microsoft Docs"
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
  - "vs.classdesigner.cpplimitation"
helpviewer_keywords: 
  - "Visual C++, Class Designer"
  - "Class Designer, Visual C++ support"
  - "Class Designer, limitations"
  - "Class Designer, tasks in Visual C++"
  - "Visual C++, class diagrams"
  - "C++, class diagrams"
  - "C++, Class Designer"
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
caps.latest.revision: 23
caps.handback.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Working with Visual C++ Code (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Klassen\-Designer zeigt eine visuelle Entwurfsoberfläche, ein sogenanntes *Klassendiagramm*, die eine visuelle Darstellung der Codeelemente in Ihrem Projekt bietet.  Sie können mit Klassendiagrammen Klassen und andere Typen in einem Projekt entwerfen und visualisieren.  
  
 Klassen\-Designer unterstützt die folgenden C\+\+\-Codeelemente:  
  
-   Klasse \(ähnlich eine verwalteten Klassenform, außer dass sie mehrere Vererbungsbeziehungen haben kann\)  
  
-   Anonyme Klasse \(zeigt den von der Klassenansicht generierten Namen für den anonymen Typ an\)  
  
-   Vorlagenklasse  
  
-   Struktur  
  
-   Enum  
  
-   Makro \(zeigt die Ansicht des Makros nach der Verarbeitung an\)  
  
-   TypeDef  
  
> [!NOTE]
>  Dies ist nicht identisch mit dem UML\-Klassendiagramm, das Sie in einem Modellierungsprojekt erstellt können.  Weitere Informationen finden Sie unter [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md).  
  
## Behandlung von Problemen bei der Typauflösung und Anzeige  
  
### Speicherort der Quelldateien  
 Klassen\-Designer merkt sich nicht den Speicherort der Quelldateien.  Wenn Sie die Projektstruktur ändern oder Quelldateien im Projekt verschieben, kann Klassen\-Designer daher den Typ "vergessen" \(insbesondere den Quelltyp einer TypeDef, von Basisklassen oder von Zuordnungstypen\).  Sie erhalten möglicherweise eine Fehlermeldung wie z. B. "**Class Designer is unable to display this type**".  In diesem Fall ziehen Sie den geänderten oder verschobenen Quellcode in das Klassendiagramm, um ihn erneut anzuzeigen.  
  
### Aktualisierungs\- und Leistungsprobleme  
 Bei Visual C\+\+\-Projekten kann es zwischen 30 und 60 Sekunden dauern, bis eine Änderung in der Quelldatei im Klassendiagramm angezeigt wird.  Diese Verzögerung kann auch dazu führen, dass Klassen\-Designer den Fehler "**No types were found in the selection**" auslöst.  Wenn Sie einen solchen Fehler erhalten, klicken Sie in der Fehlermeldung auf **Abbrechen**, und warten Sie darauf, dass das Codeelement in der Klassenansicht angezeigt wird.  Danach sollte der Klassen\-Designer den Typ anzeigen können.  
  
 Wenn ein Klassendiagramm nicht mit den Änderungen aktualisiert wird, die Sie im Code vorgenommen haben, müssen Sie möglicherweise das Diagramm schließen und erneut öffnen.  
  
### Probleme bei der Typauflösung  
 Klassen\-Designer kann aus den folgenden Gründen Typen möglicherweise nicht auflösen:  
  
-   Der Typ ist in einem Projekt oder einer Assembly, auf das\/die nicht aus dem Projekt mit dem Klassendiagramm verwiesen wird.  Um diesen Fehler zu beheben, fügen Sie einen Verweis auf das Projekt oder die Assembly mit dem Typ hinzu.  Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
-   Der Typ ist nicht im richtigen Bereich, sodass Klassen\-Designer ihn nicht finden kann.  Stellen Sie sicher, dass dem Code nicht eine Anweisung `using`, `imports`, oder `#include` fehlt.  Stellen Sie außerdem sicher, dass Sie den Typ \(oder einen zugehörigen Typ\) nicht aus dem Namespace verschoben haben, in dem er sich ursprünglich befand.  
  
-   Der Typ ist nicht vorhanden \(oder wurde auskommentiert\).  Stellen Sie zum Beheben dieses Fehlers sicher, dass Sie den Typ nicht gelöscht oder auskommentiert haben.  
  
-   Der Typ befindet sich in einer Bibliothek, auf die mit einer \#import\-Direktive verwiesen wird.  Eine mögliche Problemumgehung besteht darin, den generierten Code \(die TLH\-Datei\) manuell zu einer \#include\-Direktive in der Headerdatei hinzufügen.  
  
 Am wahrscheinlichsten wird der folgende Fehler angezeigt: **Code could not be found for one or more shapes in class diagram '\<element\>'**.  Diese Fehlermeldung besagt nicht notwendigerweise, dass der Code fehlerhaft ist.  Es gibt nur an, dass Klassen\-Designer den Code nicht anzeigen kann.  Versuchen Sie folgende Maßnahmen:  
  
-   Stellen Sie sicher, dass der Typ vorhanden ist.  Stellen Sie sicher, dass Sie den Quellcode nicht versehentlich auskommentiert oder gelöscht haben.  
  
-   Stellen Sie sicher, dass Klassen\-Designer den von Ihnen eingegebenen Typ unterstützt.  Siehe [Einschränkungen für C\+\+\-Codeelemente](#limitations).  
  
-   Versuchen Sie, den Typ aufzulösen.  Der Typ befindet sich möglicherweise in einem Projekt oder einer Assembly, auf das\/die nicht aus dem Projekt mit dem Klassendiagramm verwiesen wird.  Um diesen Fehler zu beheben, fügen Sie einen Verweis auf das Projekt oder die Assembly mit dem Typ hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds "Verweise hinzufügen"](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
-   Stellen Sie sicher, dass sich der Typ im richtigen Bereich befindet, sodass Klassen\-Designer ihn finden kann.  Stellen Sie sicher, dass dem Code nicht eine Anweisung `using`, `imports`, oder `#include` fehlt.  Stellen Sie außerdem sicher, dass Sie den Typ \(oder einen zugehörigen Typ\) nicht aus dem Namespace verschoben haben, in dem er sich ursprünglich befand.  
  
### Problembehandlung bei anderen Fehlermeldungen  
 Hilfe bei der Problembehandlung für Fehler und Warnungen finden Sie in den öffentlichen Foren von MSDN \(Microsoft Developer Network\).  Siehe dass [Visual Studio\-Klassen\-Designer\-Forum](http://go.microsoft.com/fwlink/?linkid=160754).  
  
##  <a name="limitations"></a> Einschränkungen für C\+\+\-Codeelemente  
  
-   Wenn ein Visual C\+\+\-Projekt geladen ist, funktioniert Klassen\-Designer in einem schreibgeschützten Modus.  Sie können das Klassendiagramm ändern, aber keine Änderungen am Klassendiagramm im Quellcode speichern.  
  
-   Klassen\-Designer unterstützt nur die systemeigene C\+\+\-Semantik.  Für Visual C\+\+\-Projekte, die in verwaltetem Code kompiliert werden, visualisiert Klassen\-Designer nur Codeelemente, die systemeigene Typen sind.  Daher können Sie zwar ein Klassendiagramm zu einem Projekt hinzufügen, aber Klassen\-Designer visualisiert keine Elemente, in denen die `IsManaged`\-Eigenschaft auf "`true`" festgelegt ist \(d. h. Werttypen und Referenztypen\).  
  
-   Für Visual C\+\+\-Projekten liest der Klassen\-Designer nur die Definition des Typs.  Nehmen wir beispielsweise an, dass Sie einen Typ in einer Headerdatei \(. h\) und dessen Member in einer Implementierungsdatei \(.cpp\) definieren.  Wenn Sie "Klassendiagramm anzeigen" für die Implementierungsdatei \(.cpp\) aufrufen, zeigt der Klassen\-Designer nichts an.  Ein weiteres Beispiel: Wenn Sie "Klassendiagramm anzeigen" für eine CPP\-Datei aufrufen, die eine `#include`\-Anweisung zum Einschließen anderer Dateien verwendet, aber keine eigentlichen Klassendefinitionen enthält, zeigt der Klassen\-Designer erneut nichts an.  
  
-   IDL\-Dateien \(.idl\), die COM\-Schnittstellen und Typbibliotheken definieren, werden in Diagrammen nicht angezeigt, sofern sie nicht in systemeigenen C\+\+\-Code kompiliert werden.  
  
-   Klassen\-Designer unterstützt keine globale Funktionen und Variablen.  
  
-   Klassen\-Designer unterstützt keine Unions.  Dies ist eine besondere Art von Klasse, bei der der zugeordnete Arbeitsspeicher nur so groß wie der größte Datenmember der Union ist.  
  
-   Klassen\-Designer zeigt keine grundlegenden Datentypen wie `int` und `char` an.  
  
-   Klassen\-Designer zeigt keine Typen an, die außerhalb des aktuellen Projekts definiert sind, wenn das Projekt keinen richtigen Verweise auf diese Typen besitzt.  
  
-   Klassen\-Designer kann geschachtelte Typen anzeigen, jedoch keine Beziehungen zwischen einem geschachtelten Typ und anderen Typen.  
  
-   Klassen\-Designer kann keine Typen anzeigen, die "void" sind oder von einem void\-Typ abgeleitet sind.  
  
## Siehe auch  
 [Designing and Viewing Classes and Types](../ide/designing-and-viewing-classes-and-types.md)   
 [Working with Classes and Other Types \(Class Designer\)](../ide/working-with-classes-and-other-types-class-designer.md)   
 [Working with Class Diagrams \(Class Designer\)](../ide/working-with-class-diagrams-class-designer.md)   
 [Designing Classes and Types \(Class Designer\)](../ide/designing-classes-and-types-class-designer.md)   
 [Additional Information About Class Designer Errors](../ide/additional-information-about-class-designer-errors.md)   
 [Visual C\+\+ Classes in Class Designer](../ide/visual-cpp-classes-in-class-designer.md)   
 [Visual C\+\+ Structures in Class Designer](../ide/visual-cpp-structures-in-class-designer.md)   
 [Visual C\+\+ Enumerations in Class Designer](../ide/visual-cpp-enumerations-in-class-designer.md)   
 [Visual C\+\+ Typedefs in Class Designer](../ide/visual-cpp-typedefs-in-class-designer.md)