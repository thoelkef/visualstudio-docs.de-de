---
title: "Führen Sie eine lokale Variable - Generierung von Code (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67302893dbebb65316b9c2aab09f70ddaa3e6567
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="introduce-a-local-variable-in-visual-basic"></a>Stellen Sie eine lokale Variable in Visual Basic vor.
**Was:** können Sie eine lokale Variable, um einen vorhandenen Ausdruck ersetzen sofort zu generieren.

**Wann:** Sie die standardcodezeile später problemlos konnte wäre es in einer lokalen Variablen haben.  

**Grund:** Sie kopieren und fügen Sie den Code mehrmals zu dessen Verwendung in verschiedenen Speicherorten jedoch wäre es besser, führen Sie den Vorgang nach, speichert das Ergebnis in einer lokalen Variablen und die lokale Variable Throughought verwenden könnten. 

**Vorgehensweise:**

1. Markieren Sie den Ausdruck, den Sie eine neue lokale Variable zuweisen möchten.

   ![Hervorgehobene code](media/local_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** , und wählen Sie im Menü  **einführen lokalen (aller Vorkommen der) "*Ausdruck*" ** aus Popup-Fenster "Vorschau", in dem *Ausdruck* ist der Code, die Sie ausgewählt haben.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** , und wählen Sie im Menü  **einführen lokalen (aller Vorkommen der) "*Ausdruck*" ** aus Popup-Fenster "Vorschau" wobei *Ausdruck* ist der Code, die Sie ausgewählt haben.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor bereits in der Zeile mit die rote Wellenlinie vorhanden ist.

   ![Führen Sie die lokale Vorschau](media/local_preview.png)

   >[!TIP]
   >Verwenden der [ **Vorschau der Änderungen** ](../../ide/preview-changes.md) Link am unteren Rand des Vorschaufensters, um alle Änderungen anzuzeigen, die vorgenommen wird, bevor Sie Ihre Auswahl getroffen haben.

1. Die lokale Variable wird mit dem Datentyp abgeleitet aus seiner Verwendung automatisch erstellt.  Geben Sie den neuen lokalen Variablen einen neuen Namen durch Eingabe.

   ![Stellen Sie lokalen Ergebnis vor.](media/local_result.png)

   >[!NOTE]
   >Sie können die **.. geöffnet. alle Vorkommnisse von...**  Menüoption, um jede Instanz des ausgewählten Ausdrucks gefunden wird, nicht nur die Aktivität ersetzen Sie insbesondere hervorgehoben.

## <a name="see-also"></a>Siehe auch  
[Codegenerierung (Visual Basic)](../code-generation-vb.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md) 