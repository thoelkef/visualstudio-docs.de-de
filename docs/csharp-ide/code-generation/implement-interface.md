---
title: Implementieren eine Schnittstelle - Generierung von Code (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e37cda45519062564e45127f8b8f329b75caa9a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="implement-an-interface-in-c"></a>Implementieren einer Schnittstelle in c# #
**Was:** können Sie den Code erforderlich, um eine Schnittstelle zu implementieren sofort zu generieren. 

**Wann:** von einer Schnittstelle erben sollen.  

**Grund:** Sie konnte manuell implementieren alle Schnittstelle nacheinander, aber diese Funktion automatisch alle Methodensignaturen generiert. 

**Vorgehensweise:**

1. Platzieren Sie den Cursor in der Zeile, in dem es eine rote Wellenlinie, der angibt, Sie haben eine Schnittstelle verwiesen, aber es wurden nicht alle erforderlichen Elemente implementiert ist.

   ![Hervorgehobene code](media/interface_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **Schnittstelle (explizit) implementieren** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** Menü **Schnittstelle (explizit) implementieren** im Popupmenü Fenster Vorschau.
     * Die rote Wellenlinie zeigen, und klicken Sie auf der ![Glühbirne](media/bulb.png) Symbol "angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor bereits in der Zeile mit die rote Wellenlinie vorhanden ist.

   ![Vorschau der implementieren-Klasse](media/interface_preview.png)

   >[!TIP]
   >Verwenden der [ **Vorschau der Änderungen** ](../../ide/preview-changes.md) Link am unteren Rand des Vorschaufensters, um alle Änderungen anzuzeigen, die vorgenommen wird, bevor Sie Ihre Auswahl getroffen haben.
   >
   >Darüber hinaus können Sie die **Dokument**, **Projekt**, und **Lösung** Verknüpfungen am unteren Rand des Vorschaufensters die richtigen Methodensignaturen für mehrere erstellen Klassen, die die Schnittstelle implementieren.

1. Die Schnittstelle Methodensignaturen werden automatisch erstellt, implementiert werden.

   ![Implementieren Sie die Klasse Ergebnis](media/interface_result.png)

   >[!TIP]
   >Verwenden der **Schnittstelle explizit implementieren** Option aus, um jede voranzustellen generiert die Methode mit dem Schnittstellennamen, um Namenskonflikte zu vermeiden.
   >
   >![Schnittstelle implementieren explizit führen](media/interface_explicitresult.png); 

## <a name="see-also"></a>Siehe auch  
[Codegenerierung (C#)](../code-generation-csharp.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)  
