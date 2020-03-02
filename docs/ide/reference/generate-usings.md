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
ms.openlocfilehash: f3b3435e10d6bb9a71fd16b9286759b136c167f4
ms.sourcegitcommit: ea5e02720d71185f8e27fbea205024371b0c7ceb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544546"
---
# <a name="add-missing-usings-in-visual-studio"></a>Hinzufügen fehlender using-Anweisungen in Visual Studio

Diese Codegenerierung gilt für:

- C#

**Beschreibung:** Ermöglicht Ihnen das sofortige Hinzufügen erforderlicher Import- oder [Using-Anweisungen](/dotnet/csharp/language-reference/keywords/using-directive) für kopierten und eingefügten Code.

**Hintergrund:** Es ist üblich, Code aus anderen Dateien in Ihrem Projekt oder anderen Quellen zu kopieren und in neuen Code einzufügen. Diese Schnellaktion findet fehlende Import-Anweisungen für Code, der kopiert und eingefügt wurde, und fordert Sie dann dazu auf, sie hinzuzufügen. Diese Codekorrektur kann auch Verweise von einem Projekt auf ein anderes Projekt hinzufügen.

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
