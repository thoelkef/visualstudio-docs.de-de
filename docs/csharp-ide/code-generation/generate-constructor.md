---
title: Generieren Sie einen Konstruktor - Generierung von Code (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31b0a187e0640a94d9401a1e20fd03d81ff5b920
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-constructor-in-c"></a>Generieren Sie einen Konstruktor in c# #
**Was:** können Sie sofort den Code für einen neuen Konstruktor für eine Klasse zu generieren. 

**Wann:** Sie einen neuen Konstruktor einführen und ordnungsgemäß, automatisch deklarieren möchten.  

**Grund:** konnten Sie den Konstruktor vor dem verwenden, deklarieren, aber dieses Feature, mit den entsprechenden Parametern automatisch generiert. 

**Vorgehensweise:**

1. Platzieren Sie den Cursor in der Zeile, in dem es eine rote Wellenlinie, der angibt, Sie verwendet haben, einen Konstruktor, der noch nicht vorhanden ist.

   ![Hervorgehobene code](media/constructor_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü  **generieren Konstruktor in "*TypeName*" ** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** , und wählen Sie im Menü  **generieren Konstruktor in "*TypeName*" ** im Popupmenü Fenster Vorschau.
     * Die rote Wellenlinie zeigen, und klicken Sie auf der ![Glühbirne](media/bulb.png) Symbol "angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor bereits in der Zeile mit die rote Wellenlinie vorhanden ist.

   ![Konstruktor Vorschau generieren](media/constructor_preview.png)

   >[!TIP]
   >Verwenden der [ **Vorschau der Änderungen** ](../../ide/preview-changes.md) Link am unteren Rand des Vorschaufensters, um alle Änderungen anzuzeigen, die vorgenommen wird, bevor Sie Ihre Auswahl getroffen haben.

1. Der Konstruktor wird automatisch mit allen Parametern abgeleitet aus seiner Verwendung erstellt.

   ![Konstruktorergebnis generieren](media/constructor_result.png)
  
## <a name="see-also"></a>Siehe auch  
[Codegenerierung (C#)](../code-generation-csharp.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)