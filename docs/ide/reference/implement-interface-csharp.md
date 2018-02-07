---
title: "Implementieren einer Schnittstelle – Codegenerierung (C#) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 908e11da78b2a83fb3da23d28b5cc52613f7b0f2
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2018
---
# <a name="implement-an-interface-in-c"></a>Implementieren einer Schnittstelle in C# #
**Beschreibung**: Hiermit können Sie sofort den für die Implementierung einer Schnittstelle erforderlichen Code generieren. 

**Hintergrund**: Sie möchten von einer Schnittstelle erben.  

**Vorteile**: Sie könnten nacheinander alle Schnittstellen manuell implementieren, doch bei diesem Feature werden alle Methodensignaturen automatisch generiert. 

**Vorgehensweise**:

1. Platzieren Sie den Cursor in die Zeile mit einer roten Wellenlinie, die darauf hinweist, dass Sie auf eine Schnittstelle verwiesen, jedoch nicht alle erforderlichen Member implementiert haben.

   ![Markierter Code](media/interface-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Schnittstelle explizit implementieren** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Schnittstelle explizit implementieren** aus.
     * Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-cs.png) das angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

   ![Vorschau der Aktion zum Implementieren einer Klasse](media/interface-preview-cs.png)

   >[!TIP]
   >Klicken Sie im unteren Bereich des Vorschaufensters auf den Link [**Vorschau der Änderungen**](../../ide/preview-changes.md), um vor einer Auswahl alle Änderungen anzuzeigen, die vorgenommen werden.
   >
   >Darüber hinaus können Sie am unteren Rand des Vorschaufensters auf die Links **Dokument**, **Projekt** und **Projektmappe** klicken, um die richtigen Methodensignaturen für verschiedene Klassen, die die Schnittstelle implementieren, zu erstellen.

1. Die Methodensignaturen der Schnittstelle werden automatisch erstellt und stehen für die Implementierung zur Verfügung.

   ![Ergebnis der Aktion zum Implementieren einer Klasse](media/interface-result-cs.png)

   >[!TIP]
   >Verwenden Sie die Option **Schnittstelle explizit implementieren**, um jeder generierten Methode den Schnittstellennamen voranzustellen und so Namenskonflikte zu vermeiden.
   >
   >![Schnittstelle explizit implementieren – Ergebnis](media/interface-explicitresult-cs.png); 

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)  
