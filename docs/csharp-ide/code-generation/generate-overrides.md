---
title: "Generieren von Equals und GetHashCode-Methode überschreibt - Generierung von Code (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.openlocfilehash: 88ebbeed4af1d0ea79a27ff21f7ae38ec8c252c1
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2017
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Generieren von Equals und GetHashCode-Methode überschreibt die in c# #

**Was:** können Sie generieren **gleich** und **GetHashCode** Methoden.

**Wann:** diese Außerkraftsetzungen zu generieren, wenn Sie einen Typ, die ein "Value", die nach Feldern aufweisen, anstelle von vom Speicherort des Objekts im Arbeitsspeicher zu vergleichende darstellt.

**Grund:** , wenn Sie einen Werttyp implementieren, sollten Sie erwägen, Überschreiben der Equals-Methode, um über die standardmäßige Implementierung des Equals-Methode auf ValueType eine höhere Leistung zu erhalten.

Wenn Sie einen Verweistyp implementieren, sollten Sie erwägen, Überschreiben der Equals-Methode, wenn ein Basistyp, z. B. Point, String, BigNumber usw. Ihres Typs aussieht.

Überschreiben Sie die GetHashCode-Methode, um ein Typ in einer Hashtabelle ordnungsgemäß funktioniert. Lesen Sie weitere Anleitungen auf [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators).

**Vorgehensweise:**

1. Platzieren Sie den Cursor in der Typdeklaration.

   ![Hervorgehobene code](media/overrides_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **generieren Equals(object)** oder **generieren Equals und GetHashCode** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** Menü **generieren Equals(object)** oder **generieren Equals und GetHashCode** über das untenstehende Vorschaufenster Popupfenster.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor bereits in der Zeile mit der Deklaration des Typs ist.

   ![Außerkraftsetzungen Vorschau generieren](media/overrides_preview.png)

1. Wählen Sie aus, welche Elemente, die Sie die Außerkraftsetzungen Methoden zum generieren möchten:

    ![Generieren von Außerkraftsetzungen-Dialogfeld](media/overrides_dialog.png)

    > [!TIP]
    > Sie könne auch Operatoren mithilfe der Kontrollkästchen unter der Liste der Elemente in diesem Dialogfeld zu generieren.

1. Gleich und GetHashCode automatische standardimplementierungen Außerkraftsetzungen generiert werden.

   ![Methodenergebnis generieren](media/overrides_result.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung (C#)](../code-generation-csharp.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)
