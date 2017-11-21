---
title: Implementieren einer abstrakten Klasse - Generierung von Code (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 68f60b6159cad7f751dfc47a8af116ef33a164c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="implement-an-abstract-class-in-visual-basic"></a>Implementieren einer abstrakten Klasse in Visual Basic
**Was:** können Sie den Code erforderlich, um eine abstrakte Klasse implementieren sofort zu generieren. 

**Wann:** von einer abstrakten Klasse erben sollen.  

**Grund:** konnte Sie alle abstrakten Member nacheinander, manuell implementieren, aber diese Funktion automatisch alle Methodensignaturen generiert. 

**Vorgehensweise:**

1. Platzieren Sie den Cursor in der Zeile, in dem es ist eine rote Wellenlinie, der angibt, von einer abstrakten Klasse geerbt, jedoch nicht alle erforderlichen Member implementiert haben.

   ![Hervorgehobene code](media/abstract_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **abstrakte Klasse implementieren** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** Menü **abstrakte Klasse implementieren** im Popupmenü Fenster Vorschau.
     * Die rote Wellenlinie zeigen, und klicken Sie auf der ![Glühbirne](media/bulb.png) Symbol "angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor bereits in der Zeile mit die rote Wellenlinie vorhanden ist.

   ![Vorschau der implementieren-Klasse](media/abstract_preview.png)

   >[!TIP]
   >Verwenden der [ **Vorschau der Änderungen** ](../../ide/preview-changes.md) Link am unteren Rand des Vorschaufensters, um alle Änderungen anzuzeigen, die vorgenommen wird, bevor Sie Ihre Auswahl getroffen haben.
   >
   >Darüber hinaus können Sie die **Dokument**, **Projekt**, und **Lösung** Verknüpfungen am unteren Rand des Vorschaufensters die richtigen Methodensignaturen für mehrere erstellen Klassen, die von der abstrakten Klasse erben.

1. Die abstrakte Methodensignaturen werden automatisch erstellt, implementiert werden.

   ![Implementieren Sie die Klasse Ergebnis](media/abstract_result.png)

## <a name="see-also"></a>Siehe auch  
[Codegenerierung (Visual Basic)](../code-generation-vb.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)