---
title: Arbeiten mit Visual C++-Code (Klassen-Designer) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5a543e7a1e2aca4590df320261aef2c653a55132
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662605"
---
# <a name="working-with-visual-c-code-class-designer"></a>Arbeiten mit Visual C++-Code (Klassen-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klassen-Designer zeigt eine visuelle Entwurfsoberfläche, ein sogenanntes *Klassendiagramm*, die eine visuelle Darstellung der Codeelemente in Ihrem Projekt bietet. Sie können mit Klassendiagrammen Klassen und andere Typen in einem Projekt entwerfen und visualisieren.

 Klassen-Designer unterstützt die folgenden C++-Codeelemente:

- Klasse (ähnlich eine verwalteten Klassenform, außer dass sie mehrere Vererbungsbeziehungen haben kann)

- Anonyme Klasse (zeigt den von der Klassenansicht generierten Namen für den anonymen Typ an)

- Vorlagenklasse

- Struktur

- Enum

- Makro (zeigt die Ansicht des Makros nach der Verarbeitung an)

- TypeDef

> [!NOTE]
> Dies ist nicht identisch mit dem UML-Klassendiagramm, das Sie in einem Modellierungsprojekt erstellt können. Weitere Informationen finden Sie unter [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md).

## <a name="troubleshooting-type-resolution-and-display-issues"></a>Behandlung von Problemen bei der Typauflösung und Anzeige

### <a name="location-of-source-files"></a>Speicherort der Quelldateien
 Klassen-Designer merkt sich nicht den Speicherort der Quelldateien. Wenn Sie die Projektstruktur ändern oder Quelldateien im Projekt verschieben, kann Klassen-Designer daher den Typ "vergessen" (insbesondere den Quelltyp einer TypeDef, von Basisklassen oder von Zuordnungstypen). Es wird möglicherweise ein Fehler angezeigt, z.B. **Dieser Typ kann im Klassen-Designer nicht angezeigt werden**. In diesem Fall ziehen Sie den geänderten oder verschobenen Quellcode in das Klassendiagramm, um ihn erneut anzuzeigen.

### <a name="update-and-performance-issues"></a>Aktualisierungs- und Leistungsprobleme
 Bei Visual C++-Projekten kann es zwischen 30 und 60 Sekunden dauern, bis eine Änderung in der Quelldatei im Klassendiagramm angezeigt wird. Diese Verzögerung kann auch dazu führen, dass Klassen-Designer den Fehler **In der Auswahl wurden keine Typen gefunden** auslöst. Wenn Sie einen solchen Fehler erhalten, klicken Sie in der Fehlermeldung auf **Abbrechen**, und warten Sie darauf, dass das Codeelement in der Klassenansicht angezeigt wird. Danach sollte der Klassen-Designer den Typ anzeigen können.

 Wenn ein Klassendiagramm nicht mit den Änderungen aktualisiert wird, die Sie im Code vorgenommen haben, müssen Sie möglicherweise das Diagramm schließen und erneut öffnen.

### <a name="type-resolution-issues"></a>Probleme bei der Typauflösung
 Klassen-Designer kann aus den folgenden Gründen Typen möglicherweise nicht auflösen:

- Der Typ ist in einem Projekt oder einer Assembly, auf das/die nicht aus dem Projekt mit dem Klassendiagramm verwiesen wird. Um diesen Fehler zu beheben, fügen Sie einen Verweis auf das Projekt oder die Assembly mit dem Typ hinzu. Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box (Vorgehensweise: Hinzufügen und Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“)](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

- Der Typ ist nicht im richtigen Bereich, sodass Klassen-Designer ihn nicht finden kann. Stellen Sie sicher, dass dem Code nicht eine Anweisung `using`, `imports`, oder `#include` fehlt. Stellen Sie außerdem sicher, dass Sie den Typ (oder einen zugehörigen Typ) nicht aus dem Namespace verschoben haben, in dem er sich ursprünglich befand.

- Der Typ ist nicht vorhanden (oder wurde auskommentiert). Stellen Sie zum Beheben dieses Fehlers sicher, dass Sie den Typ nicht gelöscht oder auskommentiert haben.

- Der Typ befindet sich in einer Bibliothek, auf die mit einer #import-Direktive verwiesen wird. Eine mögliche Problemumgehung besteht darin, den generierten Code (die TLH-Datei) manuell zu einer #include-Anweisung in der Headerdatei hinzufügen.

  Der Fehler, der am ehesten für eine Typauflösung angezeigt wird, ist **Für mindestens eine Form im Klassendiagramm \<element>** wurde kein Code gefunden. Diese Fehlermeldung besagt nicht notwendigerweise, dass der Code fehlerhaft ist. Es gibt nur an, dass Klassen-Designer den Code nicht anzeigen kann. Versuchen Sie folgende Maßnahmen:

- Stellen Sie sicher, dass der Typ vorhanden ist. Stellen Sie sicher, dass Sie den Quellcode nicht versehentlich auskommentiert oder gelöscht haben.

- Stellen Sie sicher, dass Klassen-Designer den von Ihnen eingegebenen Typ unterstützt. Siehe [Einschränkungen für C++-Codeelemente](#limitations).

- Versuchen Sie, den Typ aufzulösen. Der Typ befindet sich möglicherweise in einem Projekt oder einer Assembly, auf das/die nicht aus dem Projekt mit dem Klassendiagramm verwiesen wird. Um diesen Fehler zu beheben, fügen Sie einen Verweis auf das Projekt oder die Assembly mit dem Typ hinzu. Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box (Vorgehensweise: Hinzufügen und Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“)](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

- Stellen Sie sicher, dass sich der Typ im richtigen Bereich befindet, sodass Klassen-Designer ihn finden kann. Stellen Sie sicher, dass dem Code nicht eine Anweisung `using`, `imports`, oder `#include` fehlt. Stellen Sie außerdem sicher, dass Sie den Typ (oder einen zugehörigen Typ) nicht aus dem Namespace verschoben haben, in dem er sich ursprünglich befand.

### <a name="troubleshooting-other-error-messages"></a>Problembehandlung bei anderen Fehlermeldungen
 Hilfe bei der Problembehandlung für Fehler und Warnungen finden Sie in den öffentlichen Foren von MSDN (Microsoft Developer Network). Weitere Informationen finden Sie im [Forum des Visual Studio-Klassen-Designers](http://go.microsoft.com/fwlink/?linkid=160754).

## <a name="limitations"></a> Einschränkungen für C++-Codeelemente

- Wenn ein Visual C++-Projekt geladen ist, funktioniert Klassen-Designer in einem schreibgeschützten Modus. Sie können das Klassendiagramm ändern, aber keine Änderungen am Klassendiagramm im Quellcode speichern.

- Klassen-Designer unterstützt nur die systemeigene C++-Semantik. Für Visual C++-Projekte, die in verwaltetem Code kompiliert werden, visualisiert Klassen-Designer nur Codeelemente, die systemeigene Typen sind. Daher können Sie zwar ein Klassendiagramm zu einem Projekt hinzufügen, aber Klassen-Designer visualisiert keine Elemente, in denen die `IsManaged`-Eigenschaft auf "`true`" festgelegt ist (d. h. Werttypen und Referenztypen).

- Für Visual C++-Projekten liest der Klassen-Designer nur die Definition des Typs. Nehmen wir beispielsweise an, dass Sie einen Typ in einer Headerdatei (. h) und dessen Member in einer Implementierungsdatei (.cpp) definieren. Wenn Sie "Klassendiagramm anzeigen" für die Implementierungsdatei (.cpp) aufrufen, zeigt der Klassen-Designer nichts an. Ein weiteres Beispiel: Wenn Sie "Klassendiagramm anzeigen" für eine CPP-Datei aufrufen, die eine `#include`-Anweisung zum Einschließen anderer Dateien verwendet, aber keine eigentlichen Klassendefinitionen enthält, zeigt der Klassen-Designer erneut nichts an.

- IDL-Dateien (.idl), die COM-Schnittstellen und Typbibliotheken definieren, werden in Diagrammen nicht angezeigt, sofern sie nicht in systemeigenen C++-Code kompiliert werden.

- Klassen-Designer unterstützt keine globale Funktionen und Variablen.

- Klassen-Designer unterstützt keine Unions. Dies ist eine besondere Art von Klasse, bei der der zugeordnete Arbeitsspeicher nur so groß wie der größte Datenmember der Union ist.

- Klassen-Designer zeigt keine grundlegenden Datentypen wie `int` und `char` an.

- Klassen-Designer zeigt keine Typen an, die außerhalb des aktuellen Projekts definiert sind, wenn das Projekt keinen richtigen Verweise auf diese Typen besitzt.

- Klassen-Designer kann geschachtelte Typen anzeigen, jedoch keine Beziehungen zwischen einem geschachtelten Typ und anderen Typen.

- Klassen-Designer kann keine Typen anzeigen, die "void" sind oder von einem void-Typ abgeleitet sind.

## <a name="see-also"></a>Siehe auch
 [Entwerfen und Anzeigen von Klassen und Typen](../ide/designing-and-viewing-classes-and-types.md) [Arbeiten mit Klassen und anderen Typen (Klassen-Designer)](../ide/working-with-classes-and-other-types-class-designer.md) arbeiten [mit Klassendiagrammen (Klassen-Designer)](../ide/working-with-class-diagrams-class-designer.md) [Entwerfen von Klassen und Typen (Klassen-Designer)](../ide/designing-classes-and-types-class-designer.md) [Weitere Informationen zu Klassen-Designer Fehler](../ide/additional-information-about-class-designer-errors.md) [visuelle C++ Klassen in Klassen-Designer](../ide/visual-cpp-classes-in-class-designer.md) [visuellen C++ Strukturen in Klassen-Designer](../ide/visual-cpp-structures-in-class-designer.md) [visuellen C++ Enumerationen in Klassen-Designer](../ide/visual-cpp-enumerations-in-class-designer.md) [Visual C++ Typedefs in Klassen-Designer](../ide/visual-cpp-typedefs-in-class-designer.md)
