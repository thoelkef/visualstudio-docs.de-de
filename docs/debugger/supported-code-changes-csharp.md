---
title: Unterstützte Codeänderungen (C# und Visual Basic) | Microsoft-Dokumentation
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
ms.openlocfilehash: f20f61ffc4a6e4105a96b58c3dc73e7154e7c9cd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60055787"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Unterstützte codeänderungen (C# und Visual Basic)
Die Funktion "Bearbeiten und Fortfahren" behandelt die meisten Arten von Codeänderungen in Methodentexten. Die meisten Änderungen außerhalb von Methodentexten sowie einige Änderungen in Methodentexten können jedoch während des Debuggens nicht übernommen werden. Wenn Sie diese nicht unterstützten Änderungen übernehmen möchten, müssen Sie das Debuggen beenden und mit einer neuen Version des Codes erneut starten.

## <a name="supported-changes-to-code"></a>Unterstützte Änderungen an code

Die folgende Tabelle zeigt die Änderungen werden möglicherweise C# und Visual Basic-Code während einer Debugsitzung ohne Neustart der Sitzungs.

|Element/Sprachfunktion|Unterstützte Bearbeitungsvorgang|Einschränkungen|
|-|-|-|
|Typen|Hinzufügen von Methoden, Felder, Konstruktoren, Et al.|[Ja](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Hinzufügen oder ändern|Nein|
|Async/await-Ausdrücke|Hinzufügen oder ändern|[Ja](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Dynamische Objekte|Hinzufügen oder ändern|Nein|
|Lambdaausdrücke|Hinzufügen oder ändern|[Ja](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|LINQ-Ausdrücke|Hinzufügen oder ändern|[Identisch mit Lambda-Ausdrücke](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Neuere Sprachfunktionen wie etwa zeichenfolgeninterpolation und Null-Bedingte Operatoren werden in der Regel von bearbeiten und Fortfahren unterstützt. Die aktuellsten Informationen finden Sie die [Enc unterstützt bearbeitet](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) Seite.

## <a name="unsupported-changes-to-code"></a>Nicht unterstützte Änderungen an code
 Die folgenden Änderungen können nicht angewendet werden, um C# und Visual Basic-Code während einer Debugsitzung:

- Änderungen an der aktuellen Anweisung oder einer beliebigen anderen aktiven Anweisung.

     Aktive Anweisungen umfassen alle Anweisungen in Funktionen der Aufrufliste, die aufgerufen wurden, um zur aktuellen Anweisung zu gelangen.

     Die aktuelle Anweisung wird im Quellcodefenster durch einen gelben Hintergrund gekennzeichnet. Andere aktive Anweisungen werden durch einen schattierten Hintergrund gekennzeichnet und sind schreibgeschützt. Diese Standardfarben können im Dialogfeld **Optionen** geändert werden.

- Die folgende Tabelle zeigt die nicht unterstützte Änderungen an Code von Language-Element.

|Element/Sprachfunktion|Nicht unterstützte Bearbeitungsvorgang|
|-|-|
|Alle Codeelemente|Umbenennen|
|Namespaces|Hinzufügen|
|Namespaces, Typen, Member|Löschen|
|Generics|Hinzufügen oder ändern|
|Schnittstellen|Ändern|
|Typen|Abstrakte oder virtuell Mitglied hinzufügen, überschreiben Sie (finden Sie unter [Details](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Typen|Destruktor hinzufügen|
|Member|Ändern Sie einen Verweis auf einen eingebetteten Interoptyp member|
|Elemente (Visual Basic)|Ändern Sie ein Element mit On Error "oder" Resume-Anweisung|
|Elemente (Visual Basic)|Ändern Sie einen Member, die eine Aggregat, Group By, einfache JOIN- oder Group Join-LINQ-Abfrage-Klausel enthält.|
|Methoden|Ändern von Signaturen|
|Methoden|Machen Sie eine abstrakte Methode werden nicht abstrakte, indem Sie durch Hinzufügen eines methodenkörpers|
|Methoden|Löschen von Methodentext|
|Attribute|Hinzufügen oder ändern|
|Ereignisse oder Eigenschaften|Ändern Sie einen Typparameter, dem Basistyp Delegattyp und Rückgabetyp |
|Operatoren "oder" Indexer|Ändern Sie einen Typparameter, dem Basistyp Delegattyp und Rückgabetyp |
|catch-Blöcke|Ändern Sie, wenn es sich um eine aktive Anweisung enthält|
|Try-Catch-finally-Blöcken|Ändern Sie, wenn es sich um eine aktive Anweisung enthält|
|Using-Anweisungen|Hinzufügen|
|asynchrone Methoden/lambdas|Ändern Sie eine asynchrone Methode/Lambda in einem Projekt auf .NET Framework 4 ausgerichtet und senken (finden Sie unter [Details](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Ändern Sie einen Iterator in einem Projekt auf .NET Framework 4 ausgerichtet und senken (finden Sie unter [Details](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|

## <a name="unsafe-code"></a>Unsicherer Code
 Änderungen an unsicherem Code unterliegen denselben Einschränkungen wie Änderungen an sicherem Code, allerdings mit einer zusätzlichen Einschränkung: Bearbeiten und Fortfahren unterstützt keine Änderungen an unsicherem Code, der in einer Methode vorhanden, die enthält die `stackalloc` Operator.

## <a name="unsupported-app-scenarios"></a>Nicht unterstützte app-Szenarien

Nicht unterstützte Anwendungen und Plattformen gehören ASP.NET 5, Silverlight 5 und Windows 8.1.

> [!NOTE]
> Unterstützt werden Apps gehören UWP in X86- und X64 apps, die auf .NET Framework 4.6 abzielen und Windows 10 desktop oder höhere Versionen, die (das .NET Framework ist nur eine desktop-Version).

## <a name="unsupported-scenarios"></a>Nicht unterstützte Szenarien
 Bearbeiten und Fortfahren steht in den folgenden Debugszenarios nicht zur Verfügung:

- Debuggen im gemischten Modus (systemeigen/verwaltet).

- SQL-Debuggen.

- Debuggen einer Dr. Watson-Sicherungskopie.

- Debuggen einer eingebetteten Laufzeitanwendung.

- Debuggen einer Anwendung mit an den Prozess anhängen (**Debuggen > an den Prozess anhängen**) anstatt die Anwendung dazu **starten** aus der **Debuggen** Menü.

- Debuggen von optimiertem Code.

- Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.

## <a name="see-also"></a>Siehe auch
- [Bearbeiten und Fortfahren (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Vorgehensweise: Verwenden von „Bearbeiten und fortfahren“ (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)