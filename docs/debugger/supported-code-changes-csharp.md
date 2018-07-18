---
title: Unterstützte Codeänderungen (C#- und Visual Basic) | Microsoft Docs
ms.custom: ''
ms.date: 10/11/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 855e8111721480b98c1395811090a54dd6e3ab2a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480533"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Unterstützte codeänderungen (C#- und Visual Basic)
Die Funktion "Bearbeiten und Fortfahren" behandelt die meisten Arten von Codeänderungen in Methodentexten. Die meisten Änderungen außerhalb von Methodentexten sowie einige Änderungen in Methodentexten können jedoch während des Debuggens nicht übernommen werden. Wenn Sie diese nicht unterstützten Änderungen übernehmen möchten, müssen Sie das Debuggen beenden und mit einer neuen Version des Codes erneut starten.

## <a name="supported-changes-to-code"></a>Unterstützte Änderungen an code

Die folgende Tabelle zeigt die Änderungen, die in c# und Visual Basic-Code während einer Debugsitzung vorgenommen werden können, ohne die Sitzung neu zu starten.

|Element/Sprachfunktion|Unterstützte Bearbeitungsvorgang|Einschränkungen|
|-|-|-|
|Typen|Hinzufügen von Methoden, Felder, Konstruktoren, Et al.|[Ja](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Hinzufügen oder ändern|Nein|
|Async/await-Ausdrücken|Hinzufügen oder ändern|[Ja](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Dynamische Objekte|Hinzufügen oder ändern|Nein|
|Lambdaausdrücke|Hinzufügen oder ändern|[Ja](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|LINQ-Ausdrücke|Hinzufügen oder ändern|[Identisch mit Lambda-Ausdrücke](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Neuere Sprachfunktionen wie zeichenfolgeninterpolierung und Null-Bedingte Operatoren werden im Allgemeinen von bearbeiten und Fortfahren unterstützt. Die aktuellsten Informationen finden Sie unter der [Enc unterstützt bearbeitet](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) Seite.

## <a name="unsupported-changes-to-code"></a>Nicht unterstützte Änderungen an code
 Die folgenden Änderungen können nicht in c# und Visual Basic-Code während einer Debugsitzung angewendet werden:  
  
-   Änderungen an der aktuellen Anweisung oder einer beliebigen anderen aktiven Anweisung.  
  
     Aktive Anweisungen umfassen alle Anweisungen in Funktionen der Aufrufliste, die aufgerufen wurden, um zur aktuellen Anweisung zu gelangen.  
  
     Die aktuelle Anweisung wird im Quellcodefenster durch einen gelben Hintergrund gekennzeichnet. Andere aktive Anweisungen werden durch einen schattierten Hintergrund gekennzeichnet und sind schreibgeschützt. Diese Standardfarben können geändert werden, der **Optionen** (Dialogfeld).

- Die folgende Tabelle zeigt die nicht unterstützte Änderungen an Code von der Language-Element.

|Element/Sprachfunktion|Nicht unterstützte Bearbeitung|
|-|-|
|Alle Codeelemente|Umbenennen|
|Namespaces|Hinzufügen|
|Namespaces, Typen, Member|Löschen|
|Generika|Hinzufügen oder ändern|
|Schnittstellen|Ändern|
|Typen|Fügen Sie abstrakten oder virtuellen Member, fügen Sie die Außerkraftsetzung (siehe [Details](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Typen|Destruktor hinzufügen|
|Member|Ändern Sie ein Element, das einen Verweis auf eine eingebettete Interop-Typ|
|Elemente (Visual Basic)|Ändern Sie ein Element mit On Error oder Resume-Anweisung|
|Elemente (Visual Basic)|Ändern Sie einen Member, die eine Aggregat, Group By, einfache JOIN- oder Group Join-LINQ-Abfrage-Klausel enthält.|
|Methoden|Ändern von Signaturen|
|Methoden|Eine abstrakte Methode werden nicht abstrakte durch Hinzufügen eines Methodentexts|
|Methoden|Löschen von Methodentext|
|Attribute|Hinzufügen oder ändern|
|Ereignisse oder Eigenschaften|Ändern Sie einen Typparameter, der Basistyp, Delegattyp, oder als Rückgabetyp |
|Operatoren oder Indexer|Ändern Sie einen Typparameter, der Basistyp, Delegattyp, oder als Rückgabetyp |
|catch-Blöcke|Ändern Sie, wenn es sich um eine aktive Anweisung enthält|
|Try-Catch-finally-Blöcke|Ändern Sie, wenn es sich um eine aktive Anweisung enthält|
|Using-Anweisungen|Hinzufügen|
|asynchrone Methoden/lambdas|Ändern Sie eine asynchrone Methode/Lambda in einem Projekt auf .NET Framework 4 abzielt und senken (finden Sie unter [Details](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Ändern von einem Iterator im ein Projekt .NET Framework 4 ausgerichtet und senken (finden Sie unter [Details](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
  
## <a name="unsafe-code"></a>Unsicherer Code  
 Bei Änderungen an unsicherem Code gibt es dieselben Einschränkungen wie bei Änderungen an sicherem Code, es gibt jedoch eine zusätzliche Einschränkung: „Bearbeiten und Fortfahren“ unterstützt keine Änderungen an unsicherem Code, der in einer Methode vorhanden ist, die den Operator `stackalloc` enthält.  

## <a name="unsupported-app-scenarios"></a>Nicht unterstützter app-Szenarien

Nicht unterstützte apps und Plattformen gehören ASP.NET 5, Silverlight 5 und Windows 8.1.

> [!NOTE]
> Apps, die unterstützt werden universelle Windows-Plattform sind, in Windows 10 und X86- und X64-apps, die auf .NET Framework 4.6 abzielen desktop oder höhere Versionen, die (das .NET Framework ist nur eine desktop-Version).
  
## <a name="unsupported-scenarios"></a>Nicht unterstützte Szenarien  
 Bearbeiten und Fortfahren steht in den folgenden Debugszenarios nicht zur Verfügung:  
  
-   Debuggen im gemischten Modus (systemeigen/verwaltet).  
  
-   SQL-Debuggen.  
  
-   Debuggen eines Dr.Watson-Dumps.  
  
-   Debuggen einer eingebetteten Laufzeitanwendung.  
  
-   Debuggen einer Anwendung mit an den Prozess anhängen (**Debuggen > an den Prozess anhängen**) anstatt die Anwendung durch auswählen **starten** aus der **Debuggen** Menü.  
  
-   Debuggen von optimiertem Code.  
  
-   Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten Sie und fortfahren Sie (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Gewusst wie: Verwenden von "Bearbeiten und Fortfahren" (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)