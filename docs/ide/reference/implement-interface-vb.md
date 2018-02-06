---
title: "Implementieren einer Schnittstelle – Codegenerierung (Visual Basic) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 990f87cd0f1abf9d4f62ecd321ef038d689b75f4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="implement-an-interface-in-visual-basic"></a>Implementieren einer Schnittstelle in Visual Basic
**Beschreibung**: Hiermit können Sie sofort den für die Implementierung einer Schnittstelle erforderlichen Code generieren. 

**Hintergrund**: Sie möchten von einer Schnittstelle erben.  

**Vorteile**: Sie könnten nacheinander alle Schnittstellen manuell implementieren, doch bei diesem Feature werden alle Methodensignaturen automatisch generiert. 

**Vorgehensweise**:

1. Platzieren Sie den Cursor in die Zeile mit einer roten Wellenlinie, die darauf hinweist, dass Sie auf eine Schnittstelle verwiesen, jedoch nicht alle erforderlichen Member implementiert haben.

   ![Markierter Code](media/interface-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Schnittstelle explizit implementieren** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Schnittstelle explizit implementieren** aus.
     * Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-vb.png) das angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-vb.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

   ![Vorschau der Aktion zum Implementieren einer Klasse](media/interface-preview-vb.png)

   >[!TIP]
   >Klicken Sie im unteren Bereich des Vorschaufensters auf den Link [**Vorschau der Änderungen**](../../ide/preview-changes.md), um vor einer Auswahl alle Änderungen anzuzeigen, die vorgenommen werden.
   >
   >Darüber hinaus können Sie am unteren Rand des Vorschaufensters auf die Links **Dokument**, **Projekt** und **Projektmappe** klicken, um die richtigen Methodensignaturen für verschiedene Klassen, die die Schnittstelle implementieren, zu erstellen.

1. Die Methodensignaturen der Schnittstelle werden automatisch erstellt und stehen für die Implementierung zur Verfügung.

   ![Ergebnis der Aktion zum Implementieren einer Klasse](media/interface-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)