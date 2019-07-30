---
title: Generieren von Using-Anweisungen
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: d971bcdaca4efdf587c7e441f1b0b28d21388dee
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416478"
---
# <a name="add-missing-usings-in-visual-studio"></a>Hinzufügen fehlender using-Anweisungen in Visual Studio

Diese Codegenerierung gilt für:

- C#

**Beschreibung:** Ermöglicht Ihnen das sofortige Hinzufügen erforderlicher Import- oder [Using-Anweisungen](/dotnet/csharp/language-reference/keywords/using-statement) für kopierten und eingefügten Code.

**Hintergrund:** Es ist üblich, Code aus anderen Dateien in Ihrem Projekt oder anderen Quellen zu kopieren und in neuen Code einzufügen. Diese Schnellaktion findet fehlende Import-Anweisungen für Code, der kopiert und eingefügt wurde, und fordert Sie dann dazu auf, sie hinzuzufügen.

**Vorteile**: Da die Schnellaktion erforderliche Import-Anweisungen automatisch hinzufügt, müssen Sie die in Ihrem Code erforderlichen `using`-Anweisungen nicht manuell kopieren.

## <a name="add-missing-usings-refactoring"></a>Refactoring: Hinzufügen fehlender using-Anweisungen

1. Kopieren Sie Code aus einer Datei, und fügen Sie ihn in eine neue Datei ohne die erforderlichen `using`-Anweisungen ein. Zusammen mit dem resultierenden Fehler wird ein Codefix angezeigt, der die fehlenden `using`-Anweisungen hinzufügt.

    > [!NOTE]
    > Sie müssen diesen Vorschlag unter **Extras > Optionen > Text-Editor > C# > Erweitert > Using-Anweisungen** aktivieren.

2. Drücken Sie STRG+., um das Menü **Schnellaktionen und Refactorings** zu öffnen.

    ![Generieren von Using-Anweisungen](media/generate-using-codefix.png)

3. Klicken Sie auf **Using \<Ihr Verweis\>;** , um den fehlenden Verweis hinzuzufügen.

    ![Ergebnisse des Generierens von Using-Anweisungen](media/generate-using-result.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
- [Tipps für .NET-Entwickler](../csharp-developer-productivity.md)
