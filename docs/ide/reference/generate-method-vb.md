---
title: "Generieren einer Methode – Codegenerierung (Visual Basic) | Microsoft-Dokumentation"
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
ms.workload: multiple
ms.openlocfilehash: 08e46cb961ecd6511f79410a7424969f2db227ed
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-method-in-visual-basic"></a>Generieren einer Methode in Visual Basic
**Beschreibung**: Hiermit können Sie sofort eine Methode zu einer Klasse hinzufügen. 

**Hintergrund**: Sie führen eine neue Methode ein, die ordnungsgemäß automatisch deklariert werden soll.  

**Vorteile**: Sie können die Methode und Parameter vor der Verwendung zwar deklarieren, bei diesem Feature wird die Deklaration jedoch automatisch generiert. 

**Vorgehensweise**:

1. Platzieren Sie den Cursor in die Zeile mit einer roten Wellenlinie, die darauf hinweist, dass Sie eine noch nicht vorhandene Methode verwendet haben.

   ![Markierter Code](media/method-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Methode generieren** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Methode generieren** aus.
     * Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-vb.png) das angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-vb.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

   ![Vorschau der Aktion zum Generieren einer Methode](media/method-preview-vb.png)

   >[!TIP]
   >Klicken Sie im unteren Bereich des Vorschaufensters auf den Link [**Vorschau der Änderungen**](../../ide/preview-changes.md), um vor einer Auswahl alle Änderungen anzuzeigen, die vorgenommen werden.

1. Die Methode wird automatisch mit den aus der Verwendung abgeleiteten Parametern erstellt.

   ![Ergebnis der Aktion zum Generieren einer Methode](media/method-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)