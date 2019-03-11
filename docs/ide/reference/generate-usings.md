---
title: Generieren von Using-Anweisungen
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 9fd34b40bdd1167eca7fa1dff8ab60bcc787b7c7
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324755"
---
# <a name="generate-usings-in-visual-studio"></a>Generieren von Using-Anweisungen in Visual Studio

Diese Codegenerierung gilt für:

- C#

**Beschreibung:** **Beschreibung:** Ermöglicht Ihnen das sofortige Hinzufügen erforderlicher Import- oder [Using-Anweisungen](/dotnet/csharp/language-reference/keywords/using-statement) für kopierten und eingefügten Code.

**Hintergrund:** Es ist üblich, Code aus anderen Dateien in Ihrem Projekt oder anderen Codequellen zu kopieren und in den Code einzufügen. Diese Schnellaktion analysiert fehlende Import-Anweisungen für Code, der kopiert und eingefügt wurde, und fordert Sie dann dazu auf, sie hinzuzufügen.

**Vorteile**: Dank dem automatischen Hinzufügen der erforderlichen Import-Anweisungen, müssen Benutzer die erforderlichen `using`-Anweisungen nicht manuell kopieren.

## <a name="generate-usings-refactoring"></a>Refactoring: Generieren von Using-Anweisungen

1. Kopieren Sie Code aus einer anderen Datei, und fügen Sie ihn ohne die erforderlichen `using`-Anweisungen ein. Bei dem Fehler wird nun ein Codefix angezeigt, der die fehlenden `using`-Anweisungen hinzufügt.

    > [!NOTE] 
    > Dieser Vorschlag muss zunächst in **Extras > Optionen > Text-Editor > C# > Erweitert > Using-Anweisungen** aktiviert werden.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** zu öffnen. 

    ![Generieren von Using-Anweisungen](media/generate-using-codefix.png)

3. Klicken Sie auf **Using \<Ihr Verweis\>;**, um den fehlenden Verweis hinzuzufügen.

    ![Ergebnisse des Generierens von Using-Anweisungen](media/generate-using-result.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
- [Tipps für .NET-Entwickler](../../ide/visual-studio-2017-for-dotnet-developers.md)