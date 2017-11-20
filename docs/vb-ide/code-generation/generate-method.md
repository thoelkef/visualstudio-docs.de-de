---
title: Generieren Sie eine Methode - Generierung von Code (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8505f9a4fa8571e0e1c1e45f092d1b0e40c8ee9b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-method-in-visual-basic"></a>Generieren Sie eine Methode in Visual Basic
**Was:** können Sie sofort eine Methode einer Klasse hinzufügen. 

**Wann:** Sie eine neue Methode eingeführt und ordnungsgemäß, automatisch deklarieren möchten.  

**Grund:** konnten Sie deklarieren Methode und der Parameter vor der Verwendung, aber diese Funktion die Deklaration automatisch generiert. 

**Vorgehensweise:**

1. Platzieren Sie den Cursor in der Zeile, in dem es eine rote Wellenlinie, der angibt, Sie verwendet haben, eine Methode, die noch nicht vorhanden ist.

   ![Hervorgehobene code](media/method_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **Generate-Methode** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** Menü **Generate-Methode** im Popupmenü Fenster Vorschau.
     * Die rote Wellenlinie zeigen, und klicken Sie auf der ![Glühbirne](media/bulb.png) Symbol "angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor bereits in der Zeile mit die rote Wellenlinie vorhanden ist.

   ![Methode Vorschau generieren](media/method_preview.png)

   >[!TIP]
   >Verwenden der [ **Vorschau der Änderungen** ](../../ide/preview-changes.md) Link am unteren Rand des Vorschaufensters, um alle Änderungen anzuzeigen, die vorgenommen wird, bevor Sie Ihre Auswahl getroffen haben.

1. Die Methode wird automatisch mit allen Parametern abgeleitet aus seiner Verwendung erstellt werden.

   ![Methodenergebnis generieren](media/method_result.png)
  
## <a name="see-also"></a>Siehe auch  
[Codegenerierung (Visual Basic)](../code-generation-vb.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)