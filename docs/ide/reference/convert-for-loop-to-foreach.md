---
title: Refactoring von Code zum Konvertieren einer for-Schleife in eine foreach-Anweisung
ms.date: 05/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 34758473bcbee8ccad7d9dff9df2f1478ca1202c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refactoring zum Konvertieren einer for-Schleife in eine foreach-Anweisung

Diese Refactorings gelten für:

- C#

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Konvertieren einer for-Schleife in eine foreach-Anweisung

Sobald Sie über eine [for](/dotnet/csharp/language-reference/keywords/for)-Schleife in Ihrem Code verfügen, können Sie dieses Refactoring verwenden, um sie in eine [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)-Anweisung zu konvertieren.

### <a name="why-convert"></a>Warum eine Konvertierung?

Die Gründe, warum Sie eine [for](/dotnet/csharp/language-reference/keywords/for)-Schleife in eine [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)-Anweisung konvertieren sollten, können wie folgt aussehen:

- Sie verwenden die Variable der Iterationsanzahl nicht innerhalb der Schleife, außer als Index, um auf das Element zuzugreifen.

- Sie möchten Ihren Code vereinfachen und die Gefahr möglicher logischer Fehler im Initialisierer, der Bedingung und der Iterationsanweisungen vermeiden.

### <a name="how-to-use-it"></a>Verwendungsweise

1. Platzieren Sie Ihren Mauszeiger auf der ersten Zeile der `for`-Schleife.

1. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, oder klicken Sie auf den Schraubendreher ![Schraubendrehersymbol](../media/screwdriver-icon.png) im Randbereich der Codedatei.

   ![Menü „In "foreach" konvertieren“](media/convert-to-foreach.png)

1. Wählen Sie **In "foreach" konvertieren** aus. Wählen Sie alternativ **Vorschau der Änderungen anzeigen** aus, um das Dialogfeld [Vorschau der Änderungen](../../ide/preview-changes.md) anzuzeigen. Klicken Sie dann auf **Anwenden**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Konvertieren einer foreach-Anweisung in eine for-Schleife

Sobald Sie über eine [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)-Anweisung in Ihrem Code verfügen, können Sie dieses Refactoring verwenden, um sie in eine [for](/dotnet/csharp/language-reference/keywords/for)-Schleife zu konvertieren.

### <a name="why-convert"></a>Warum eine Konvertierung?

Die Gründe, warum Sie eine [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)-Anweisung in eine [for](/dotnet/csharp/language-reference/keywords/for)-Schleife konvertieren sollten, können wie folgt aussehen:

- Sie möchten die Variable für die Anzahl der Iterationen innerhalb der Schleife verwenden und nicht nur einfach auf das Element zugreifen.

- Sie [durchlaufen ein multidimensionales Array](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) und möchten mehr Kontrolle über die Arrayelemente haben.

### <a name="how-to-use-it"></a>Verwendungsweise

1. Platzieren Sie Ihren Mauszeiger auf der ersten Zeile der `foreach`-Anweisung.

1. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, oder klicken Sie auf den Schraubendreher ![Schraubendrehersymbol](../media/screwdriver-icon.png) im Randbereich der Codedatei.

   ![Menü „In "for" konvertieren“](media/convert-to-for.png)

1. Wählen Sie **In "for" konvertieren** aus. Wählen Sie alternativ **Vorschau der Änderungen anzeigen** aus, um das Dialogfeld [Vorschau der Änderungen](../../ide/preview-changes.md) anzuzeigen. Klicken Sie dann auf **Anwenden**.

1. Da durch das Refactoring eine neue Variable für die Anzahl der Iterationen eingeführt wird, wird das Feld **Umbenennen** in der oberen rechten Ecke des Editors angezeigt. Wenn Sie die Variable anders benennen möchten, tippen Sie den neuen Namen ein, und drücken Sie die **EINGABETASTE**, oder wählen Sie im Feld **Umbenennen** die Option **Anwenden** aus. Wenn Sie keinen neuen Namen auswählen möchten, drücken Sie die **Esc**-Taste, oder klicken Sie auf **Anwenden**, um das Feld **Umbenennen** zu schließen.

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)