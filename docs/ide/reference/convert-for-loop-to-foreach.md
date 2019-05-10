---
title: Refactoring von Code zum Konvertieren einer for-Schleife in eine foreach-Anweisung
ms.date: 05/10/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: fc14a07557b3ae46a84f506bc0fa9007efface63
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62811888"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refactoring zum Konvertieren einer for-Schleife in eine foreach-Anweisung

Dieser Artikel beschreibt die Schnellaktion-Refactorings, die zwischen zwei Schleifenstrukturen konvertieren. Er beschreibt außerdem Gründe für den Wechsel zwischen einer [for](/dotnet/csharp/language-reference/keywords/for)-Schleife und einer [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)-Anweisung in Ihrem Code.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Konvertieren einer for-Schleife in eine foreach-Anweisung

Sobald Sie über eine [for](/dotnet/csharp/language-reference/keywords/for)-Schleife in Ihrem Code verfügen, können Sie dieses Refactoring verwenden, um sie in eine [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)-Anweisung zu konvertieren.

Dieses Refactoring gilt für:

- C#

> [!NOTE]
> Das Schnellaktion-Refactoring **Convert to foreach** (In „foreach“ konvertieren) ist nur für [for](/dotnet/csharp/language-reference/keywords/for)-Schleifen verfügbar, die alle drei Teile enthalten: einen Initialisierer, eine Bedingung und einen Iterator.

### <a name="why-convert"></a>Warum eine Konvertierung?

Die Gründe, warum Sie eine [for](/dotnet/csharp/language-reference/keywords/for)-Schleife in eine [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)-Anweisung konvertieren sollten, können wie folgt aussehen:

- Sie verwenden die lokale Schleifenvariable nicht innerhalb der Schleife, außer als Index, um auf Elemente zuzugreifen.

- Sie möchten Ihren Code vereinfachen und die Gefahr möglicher logischer Fehler im Initialisierer, in der Bedingung und im Iterator reduzieren.

### <a name="how-to-use-it"></a>Verwendungsweise

1. Platzieren Sie Ihre Einfügemarke im `for`-Schlüsselwort.

1. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, oder klicken Sie auf den Schraubendreher ![Schraubendrehersymbol](../media/screwdriver-icon.png) im Randbereich der Codedatei.

   ![Menü „In "foreach" konvertieren“](media/convert-to-foreach.png)

1. Wählen Sie **In "foreach" konvertieren** aus. Wählen Sie alternativ **Vorschau der Änderungen anzeigen** aus, um das Dialogfeld [Vorschau der Änderungen](../../ide/preview-changes.md) anzuzeigen. Klicken Sie dann auf **Anwenden**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Konvertieren einer foreach-Anweisung in eine for-Schleife

Sobald Sie über eine [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in)- oder eine [For Each...Next (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)-Anweisung in Ihrem Code verfügen, können Sie dieses Refactoring verwenden, um sie in eine [for](/dotnet/csharp/language-reference/keywords/for)-Schleife zu konvertieren.

Dieses Refactoring gilt für:

- C#

- Visual Basic

### <a name="why-convert"></a>Warum eine Konvertierung?

Die Gründe, warum Sie eine [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)-Anweisung in eine [for](/dotnet/csharp/language-reference/keywords/for)-Schleife konvertieren sollten, können wie folgt aussehen:

- Sie möchten die lokale Schleifenvariable innerhalb der Schleife verwenden und nicht nur einfach auf das Element zugreifen.

- Sie [durchlaufen ein multidimensionales Array](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) und möchten mehr Kontrolle über die Arrayelemente haben.

### <a name="how-to-use-it"></a>Verwendungsweise

1. Platzieren Sie Ihre Einfügemarke im `foreach`- oder `For Each`-Schlüsselwort.

1. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, oder klicken Sie auf den Schraubendreher ![Schraubendrehersymbol](../media/screwdriver-icon.png) im Randbereich der Codedatei.

   ![Menü „In "for" konvertieren“](media/convert-to-for.png)

1. Wählen Sie **In "for" konvertieren** aus. Wählen Sie alternativ **Vorschau der Änderungen anzeigen** aus, um das Dialogfeld [Vorschau der Änderungen](../../ide/preview-changes.md) anzuzeigen. Klicken Sie dann auf **Anwenden**.

1. Da durch das Refactoring eine neue Variable für die Anzahl der Iterationen eingeführt wird, wird das Feld **Umbenennen** in der oberen rechten Ecke des Editors angezeigt. Wenn Sie die Variable anders benennen möchten, tippen Sie den neuen Namen ein, und drücken Sie die **EINGABETASTE**, oder wählen Sie im Feld **Umbenennen** die Option **Anwenden** aus. Wenn Sie keinen neuen Namen auswählen möchten, drücken Sie die **Esc**-Taste, oder klicken Sie auf **Anwenden**, um das Feld **Umbenennen** zu schließen.

> [!NOTE]
> In C# verwendet der durch diese Refactorings generierte Code entweder einen expliziten Typ oder [var](/dotnet/csharp/language-reference/keywords/var) als Typ für die Elemente in der Auflistung. Der Typ im generierten Code, unabhängig ob explizit oder implizit, hängt von den Einstellungen des Codeformats für diesen Bereich ab. Diese bestimmten Einstellungen des Codeformats werden auf Computerebene unter **Extras** > **Optionen** > **Text-Editor** > **C#** > **Codeformat** > **Allgemein** > **\'var-Einstellungen** oder auf Projektmappenebene in einer [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types)-Datei konfiguriert. Wenn Sie die Einstellungen des Codeformats in den **Optionen** ändern, müssen Sie die Codedatei erneut öffnen, damit die Änderungen wirksam werden.

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)