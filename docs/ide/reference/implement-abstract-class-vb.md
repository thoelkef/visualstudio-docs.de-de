---
title: "Implementieren einer abstrakten Klasse – Codegenerierung (Visual Basic) | Microsoft-Dokumentation"
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
ms.workload: multiple
ms.openlocfilehash: 135c1edc6719c567e21496f047af45b7ce311d13
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="implement-an-abstract-class-in-visual-basic"></a>Implementieren einer abstrakten Klasse in Visual Basic
**Beschreibung**: Hiermit können Sie sofort den für die Implementierung einer abstrakten Klasse erforderlichen Code generieren. 

**Hintergrund**: Sie möchten von einer abstrakten Klasse erben.  

**Vorteile**: Sie könnten nacheinander alle abstrakten Member manuell implementieren, doch bei diesem Feature werden alle Methodensignaturen automatisch generiert. 

**Vorgehensweise**:

1. Platzieren Sie den Cursor in die Zeile mit einer roten Wellenlinie, die darauf hinweist, dass Sie auf eine abstrakte Klasse verwiesen, jedoch nicht alle erforderlichen Member implementiert haben.

   ![Markierter Code](media/abstract-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Abstrakte Klasse implementieren** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Abstrakte Klasse implementieren** aus.
     * Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-vb.png) das angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-vb.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

   ![Vorschau der Aktion zum Implementieren einer Klasse](media/abstract-preview-vb.png)

   >[!TIP]
   >Klicken Sie im unteren Bereich des Vorschaufensters auf den Link [**Vorschau der Änderungen**](../../ide/preview-changes.md), um vor einer Auswahl alle Änderungen anzuzeigen, die vorgenommen werden.
   >
   >Darüber hinaus können Sie am unteren Rand des Vorschaufensters auf die Links **Dokument**, **Projekt** und **Projektmappe** klicken, um die richtigen Methodensignaturen für verschiedene Klassen, die von der abstrakten Klasse erben, zu erstellen.

1. Die abstrakten Methodensignaturen werden automatisch erstellt und stehen für die Implementierung zur Verfügung.

   ![Ergebnis der Aktion zum Implementieren einer Klasse](media/abstract-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)