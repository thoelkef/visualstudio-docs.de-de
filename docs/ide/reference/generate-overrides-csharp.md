---
title: "Generieren von Equals- und GetHashCode-Methodenüberschreibungen – Codegenerierung (C#) | Microsoft-Dokumentation"
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
ms.workload: dotnet
ms.openlocfilehash: 56b1753dbdcfbf8ce318e964a16879f02b1482c4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Generieren von Equals- und GetHashCode-Methodenüberschreibungen in C# #

**Beschreibung**: Ermöglicht das Generieren von **Equals**- und **GetHashCode**-Methoden.

**Hintergrund**: Diese Überschreibungen werden für Typen generiert, die einen „Wert“ darstellen, der durch einige Felder verglichen werden soll, nicht durch die Objektposition im Arbeitsspeicher.

**Vorteile**: Wenn Sie einen Werttyp implementieren, sollten Sie erwägen, die Equals-Methode zu überschreiben, um eine bessere Leistung als mit der Standardimplementierung der Equals-Methode in ValueType zu erzielen.

Wenn Sie einen Verweistyp implementieren, sollten Sie erwägen, die Equals-Methode zu überschreiben, wenn der Typ wie ein Basistyp aussieht, z.B. Point, String, BigNumber usw.

Überschreiben Sie die GetHashCode-Methode, damit ein Typ in einer Hashtabelle ordnungsgemäß funktioniert. Informieren Sie sich weiter über [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators).

**Vorgehensweise**:

1. Platzieren Sie den Cursor in Ihre Typdeklaration.

   ![Markierter Code](media/overrides-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **"Equals(object)" generieren** oder **"Equals" und "GetHashCode" generieren** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste, wählen Sie das Menü **Schnellaktionen und Refactorings** aus, und wählen Sie im Popupvorschaufenster **"Equals(object)" generieren** oder **"Equals" und "GetHashCode" generieren** aus.
     * Klicken Sie auf das ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der Typdeklaration platziert ist.

   ![Generieren von Überschreibungen – Vorschau](media/overrides-preview-cs.png)

1. Wählen Sie die Member aus, für die Sie die Methodenüberschreibungen generieren möchten:

    ![Generieren von Überschreibungen – Dialogfeld](media/overrides-dialog-cs.png)

    > [!TIP]
    > In diesem Dialogfeld können Sie auch die Generierung von Operatoren auswählen, indem Sie die entsprechenden Kontrollkästchen unterhalb der Memberliste verwenden.

1. Die Equals- und GetHashCode-Überschreibungen werden mit automatischen Standardimplementierungen generiert.

   ![Ergebnis der Aktion zum Generieren einer Methode](media/overrides-result-cs.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)
