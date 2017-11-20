---
title: Generieren Sie ein Feld, Eigenschaft oder eine lokale - Generierung von Code (Visual Basic) | Microsoft Docs
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
ms.openlocfilehash: 2dd0ef0db74a0ee723c7cd09bd8118e646b8ba3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>Generieren Sie ein Feld, Eigenschaft oder eine lokale in Visual Basic
**Was:** können Sie den Code für eine zuvor nicht deklarierte Feld, eine Eigenschaft oder eine lokale sofort zu generieren. 

**Wann:** führen Sie ein neues Feld, Eigenschaft oder lokalen während der Eingabe und ordnungsgemäß, automatisch deklarieren möchten.  

**Grund:** konnten Sie das Feld, Eigenschaft oder lokale vor der Verwendung, aber dieses Feature die Deklaration generiert und automatisch deklarieren. 

**Vorgehensweise:**

1. Platzieren Sie den Cursor in der Zeile, in dem es ist eine rote Wellenlinie, der angibt, Sie verwendet haben, ein Feld, eine lokale oder eine Eigenschaft, die noch nicht vorhanden.

   ![Hervorgehobene code](media/field_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü  **generieren Variable "*Name*" > Feld/Eigenschaft generieren/lokale ** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** Menü  **generieren Variable "*Name*" > Feld/Eigenschaft generieren/lokale ** aus der Vorschau Fenster Popupfenster.
     * Die rote Wellenlinie zeigen, und klicken Sie auf der ![Glühbirne](media/bulb.png) Symbol "angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor bereits in der Zeile mit die rote Wellenlinie vorhanden ist.

   ![Feld/Eigenschaft/lokale Vorschau generieren](media/field_preview.png)

   >[!TIP]
   >Verwenden der [ **Vorschau der Änderungen** ](../../ide/preview-changes.md) Link am unteren Rand des Vorschaufensters, um alle Änderungen anzuzeigen, die vorgenommen wird, bevor Sie Ihre Auswahl getroffen haben.

1. Das Feld, Eigenschaft oder lokalen wird automatisch mit dem Datentyp abgeleitet aus seiner Verwendung erstellt.

   ![Feld/Eigenschaft/Local Ergebnis generieren](media/field_result.png)

## <a name="see-also"></a>Siehe auch  
[Codegenerierung (Visual Basic)](../code-generation-vb.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)