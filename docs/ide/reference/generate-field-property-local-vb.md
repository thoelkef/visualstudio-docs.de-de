---
title: "Generieren eines Felds, einer Eigenschaft oder eines lokalen Elements – Codegenerierung (Visual Basic) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 766311f0ba165c87e61bb873baa3ab2f0b2d1402
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>Generieren eines Felds, einer Eigenschaft oder eines lokalen Elements in Visual Basic
**Beschreibung**: Sie können sofort Code für ein Feld, eine Eigenschaft oder ein lokales Element generieren, das bzw. die zuvor nicht deklariert war. 

**Hintergrund**: Sie führen während der Eingabe ein neues Feld, eine neue Eigenschaft oder ein neues lokales Element ein und möchten dieses bzw. diese automatisch deklarieren.  

**Vorteile**: Sie könnten das Feld, die Eigenschaft oder das lokale Element zwar vor der Verwendung deklarieren, dieses Feature generiert Deklaration und Typ jedoch automatisch. 

**Vorgehensweise**:

1. Platzieren Sie den Cursor in die Zeile mit einer roten Wellenlinie, die darauf hinweist, dass Sie ein Feld, ein lokales Element oder eine Eigenschaft verwendet haben, das bzw. die noch nicht vorhanden ist.

   ![Markierter Code](media/field-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Variable '*Name*' generieren > Feld/Eigenschaft/Lokales Element generieren** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste, wählen Sie das Menü **Schnellaktionen und Refactorings** aus, und wählen Sie im Popupvorschaufenster **Variable '*Name*' generieren > Feld/Eigenschaft/Lokales Element generieren** aus.
     * Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-vb.png) das angezeigt wird.
     * Klicken Sie auf das ![Glühbirnensymbol,](media/bulb-vb.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

   ![Feld/Eigenschaft/Lokales Element generieren – Vorschau](media/field-preview-vb.png)

   >[!TIP]
   >Klicken Sie im unteren Bereich des Vorschaufensters auf den Link [**Vorschau der Änderungen**](../../ide/preview-changes.md), um vor einer Auswahl alle Änderungen anzuzeigen, die vorgenommen werden.

1. Das Feld, die Eigenschaft bzw. das lokale Element wird automatisch mit dem aus der Verwendung abgeleiteten Typ erstellt.

   ![Feld/Eigenschaft/Lokales Element generieren – Ergebnis](media/field-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)