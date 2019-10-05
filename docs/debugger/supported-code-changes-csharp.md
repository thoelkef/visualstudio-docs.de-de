---
title: Unterstützte Code ÄnderungenC# (und Visual Basic) | Microsoft-Dokumentation
ms.date: 10/11/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c5f54a2b50447125b0abffd8cc62ba9c2a1d2b37
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887776"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Unterstützte CodeänderungenC# (und Visual Basic)
Die Funktion "Bearbeiten und Fortfahren" behandelt die meisten Arten von Codeänderungen in Methodentexten. Die meisten Änderungen außerhalb von Methodentexten sowie einige Änderungen in Methodentexten können jedoch während des Debuggens nicht übernommen werden. Wenn Sie diese nicht unterstützten Änderungen übernehmen möchten, müssen Sie das Debuggen beenden und mit einer neuen Version des Codes erneut starten.

## <a name="supported-changes-to-code"></a>Unterstützte Änderungen am Code

In der folgenden Tabelle sind die Änderungen aufgeführt, die während C# einer Debugsitzung vorgenommen und Visual Basic werden können, ohne dass die Sitzung neu gestartet wird.

|Sprach Element/Feature|Unterstützter Bearbeitungsvorgang|Einschränkungen|
|-|-|-|
|Typen|Add Methods, Fields, Constructors, et al|[Ja](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Hinzufügen oder ändern|Nein|
|Async/Erwartung von Ausdrücken|Hinzufügen oder ändern|[Ja](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Dynamische Objekte|Hinzufügen oder ändern|Nein|
|Lambdaausdrücke|Hinzufügen oder ändern|[Ja](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|LINQ-Ausdrücke|Hinzufügen oder ändern|[Identisch mit Lambda-Ausdrücken](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Neuere sprach Features wie Zeichen folgen Interpolationen und NULL bedingte Operatoren werden in der Regel von "Bearbeiten und Fortfahren" unterstützt. Die aktuellsten Informationen finden Sie auf der Seite [unterstützte](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) bearbeitbare edits.

## <a name="unsupported-changes-to-code"></a>Nicht unterstützte Codeänderungen
 Die folgenden Änderungen können während einer Debugsitzung nicht auf C# und Visual Basic Code angewendet werden:

- Änderungen an der aktuellen Anweisung oder einer beliebigen anderen aktiven Anweisung.

     Aktive Anweisungen umfassen alle Anweisungen in Funktionen der Aufrufliste, die aufgerufen wurden, um zur aktuellen Anweisung zu gelangen.

     Die aktuelle Anweisung wird im Quellcodefenster durch einen gelben Hintergrund gekennzeichnet. Andere aktive Anweisungen werden durch einen schattierten Hintergrund gekennzeichnet und sind schreibgeschützt. Diese Standardfarben können im Dialogfeld **Optionen** geändert werden.

- In der folgenden Tabelle werden nicht unterstützte Änderungen am Code des Language-Elements angezeigt.

|Sprach Element/Feature|Nicht unterstützter Bearbeitungsvorgang.|
|-|-|
|Alle Code Elemente|Umbenennen|
|Namespaces|Hinzufügen|
|Namespaces, Typen, Member|Löschen|
|Generics|Hinzufügen oder ändern|
|Schnittstellen|Ändern|
|Typen|Abstract oder Virtual Member hinzufügen, außer Kraft Setzung hinzufügen (siehe [Details](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Typen|Destruktor hinzufügen|
|Member|Ändern eines Members, der auf einen eingebetteten Interoptyp verweist|
|Member|Ändern eines statischen Members, nachdem er durch Ausführen von Code bereits aufgerufen wurde|
|Member (Visual Basic)|Ändern eines Members mit On Error-oder Resume-Anweisung|
|Member (Visual Basic)|Ändern eines Members, der eine LINQ-Abfrage Klausel mit Aggregat-, Group by-, Simple Join-oder Group Join-Klausel enthält|
|Methoden|Signaturen ändern|
|Methoden|Eine abstrakte Methode durch Hinzufügen eines Methoden Texts als nicht abstrakt festlegen|
|Methoden|Methoden Text löschen|
|Attribute|Hinzufügen oder ändern|
|Ereignisse oder Eigenschaften|Ändern eines Typparameters, Basistyps, Delegattyps oder Rückgabe Typs |
|Operatoren oder Indexer|Ändern eines Typparameters, Basistyps, Delegattyps oder Rückgabe Typs |
|catch-Blöcke|Ändern, wenn es eine aktive Anweisung enthält|
|try-catch-endlich-Blöcke|Ändern, wenn es eine aktive Anweisung enthält|
|Using-Anweisungen|Hinzufügen|
|Async-Methoden/Lambdas|Ändern einer Async-Methode/eines Lambda-Ausdrucks in einem Projekt, das auf die .NET Framework 4 und niedriger abzielt (siehe [Details](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Ändern eines Iterators in einem Projekt, das auf .NET Framework 4 und niedriger abzielt (siehe [Details](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|

## <a name="unsafe-code"></a>Unsicherer Code
 Änderungen an unsicherem Code unterliegen denselben Einschränkungen wie Änderungen an sicherem Code, allerdings mit einer zusätzlichen Einschränkung: "Bearbeiten und Fortfahren" unterstützt keine Änderungen an unsicherem Code, der innerhalb `stackalloc` einer Methode beendet wird, die den Operator enthält.

## <a name="unsupported-app-scenarios"></a>Nicht unterstützte App-Szenarios

Nicht unterstützte apps und Plattformen sind ASP.net 5, Silverlight 5 und Windows 8.1.

> [!NOTE]
> Zu den unterstützten apps zählen UWP in Windows 10 und x86-und x64-apps, die auf den .NET Framework 4,6-Desktop oder spätere Versionen abzielen (die .NET Framework ist nur eine Desktop Version).

## <a name="unsupported-scenarios"></a>Nicht unterstützte Szenarien
 Bearbeiten und Fortfahren steht in den folgenden Debugszenarios nicht zur Verfügung:

- Debuggen im gemischten Modus (systemeigen/verwaltet).

- SQL-Debuggen.

- Debuggen einer Dr. Watson-Sicherungskopie.

- Debuggen einer eingebetteten Laufzeitanwendung.

- Debuggen einer Anwendung mit **Anfügen** an den Prozess (**debug> an den Prozess anhängen**) anstatt die Anwendung durch Auswahl von starten im Menü **Debuggen** zu starten.

- Debuggen von optimiertem Code.

- Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.

## <a name="see-also"></a>Siehe auch
- [Bearbeiten und Fortfahren (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Vorgehensweise: Verwenden von „Bearbeiten und fortfahren“ (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)