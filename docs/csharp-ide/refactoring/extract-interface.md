---
title: Extrahieren Sie die Schnittstelle - Umgestaltung (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 55e17f0a-eacb-41ec-b8ca-74f5c6bbd6de
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: csharp
ms.openlocfilehash: 854e341a5c02b3bb4b0a596720a4899410550689
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="extract-an-interface-in-c"></a>Extrahieren einer Schnittstelle in c# #
**Was:** können Sie eine Schnittstelle, die mit vorhandenen Elementen aus einer Klasse, Struktur oder Schnittstelle zu erstellen.

**Wann:** Sie haben mehrere Klassen, Strukturen oder Schnittstellen mit Methoden, die allgemeine und von anderen Klassen, Strukturen oder Schnittstellen verwendet hergestellt werden konnte.

**Grund:** Schnittstellen hervorragende Konstrukte für objektorientierte Entwürfe sind.  Stellen Sie sich vor, da Klassen für verschiedene Tieren (Hund Cat Vogel) alle allgemeine Methoden, z. B. Eat Getränken, Standbymodus möglicherweise.  Verwendung einer Schnittstelle wie IAnimal würde Hund Cat und Vogel haben eine gemeinsame "Signatur" für diese Methoden ermöglichen.  

**Vorgehensweise:**

1. Markieren Sie den Namen der Klasse, die die Aktion ausgeführt, oder platzieren Sie den Textcursor nur an einer beliebigen Stelle im Klassennamen.

   ![Hervorgehobene code](media/extractinterface_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG + R**, klicken Sie dann **STRG + I**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **Schnittstelle extrahieren** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Wählen Sie **Bearbeiten > Umgestalten > Schnittstelle extrahieren**.
     * Mit der rechten Maustaste in des Namens der Klasse, wählen die **Schnellaktionen und Refactorings** Menü **Schnittstelle extrahieren** im Popupmenü Fenster Vorschau.

1. In der **Schnittstelle extrahieren** gestartet wurde, jetzt angezeigten Dialogfeld Geben Sie die Informationen aufgefordert: ![Schnittstelle extrahieren](media/extractinterface_dialog.png)
   | Feld | Beschreibung |
   | --- | --- |
   | **Name der neuen Schnittstelle** | Der Name der Schnittstelle erstellt werden soll. Dies wird standardmäßig ich*ClassName*, wobei *ClassName* ist der Name der Klasse, die Sie oben ausgewählt. |
   | **Neuen Dateinamen** | Der Name der Datei, die generiert wird, die die Schnittstelle enthält. Wie mit dem Schnittstellennamen, dies ich standardmäßig generiert*ClassName*, wobei *ClassName* ist der Name der Klasse, die Sie oben ausgewählt. |
   | **Öffentliche Member zum bilden einer Schnittstelle auswählen** | Die Elemente, die in der Schnittstelle extrahieren.  Sie können beliebig viele beliebig auswählen. |

1. Klicken Sie auf **OK**.

   Die Schnittstelle wird sofort in der Datei mit dem angegebenen Namen erstellt werden.  Darüber hinaus wird die ausgewählte Klasse jetzt diese Schnittstelle implementieren.

   ![Resultierende Klasse](media/extractinterface_class.png)
   ![resultierende-Schnittstelle](media/extractinterface_interface.png)

## <a name="see-also"></a>Siehe auch  
[Refactoring (C#)](../refactoring-csharp.md)