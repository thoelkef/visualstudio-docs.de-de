---
title: "Zugehörige Datei - Umgestaltung (c#) Typ ans | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f58c34-c50f-4297-91b2-2e243380dcc9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9fa5a15f9c8e688c973594309efbfa6cb5d10e8b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="move-a-type-to-a-matching-file-in-c"></a>Verschieben eines Typs in eine entsprechende Datei in c# #
**Was:** können Sie den ausgewählten Typ in eine separate Datei mit demselben Namen zu verschieben.

**Wann:** stehen Ihnen mehrere Klassen, Strukturen, Schnittstellen usw. in der gleichen Datei, die Sie trennen möchten.  

**Grund:** mehrere Typen in der gleichen Datei platzieren kann erschweren dieser Typen zu suchen.  Typen in Dateien mit demselben Namen verschieben, wird Code besser lesbar und einfacher zu navigieren.

**Vorgehensweise:**

1. Markieren Sie, oder platzieren Sie den Textcursor innerhalb der Name des Typs zu verschieben:

   ![Hervorgehobene code](media/movetype_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** , und wählen Sie im Menü **Typ verschieben *TypeName*cs** aus Popup-Fenster "Vorschau", in dem *TypeName* ist der Name des Typs, die Sie ausgewählt haben.
   * **Maus**
     * Mit der rechten Maustaste in des Codes, wählen Sie die **Schnellaktionen und Refactorings** , und wählen Sie im Menü **Typ zu verschieben *TypeName*cs** aus Popup-Fenster "Vorschau", in dem  *TypeName* ist der Name des Typs, die Sie ausgewählt haben.

   Der Typ wird sofort in eine neue Datei mit diesem Namen innerhalb der Projektmappe verschoben.

   ![Inline-Ergebnis](media/movetype_result.png)

## <a name="see-also"></a>Siehe auch  
[Refactoring (C#)](../refactoring-csharp.md)