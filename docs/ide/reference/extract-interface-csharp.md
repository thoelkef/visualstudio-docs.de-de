---
title: Extrahieren einer Schnittstelle in C# | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 0e763bacb6d900fea251b3c41d33fb464479f2c4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="extract-an-interface-in-c"></a>Extrahieren einer Schnittstelle in C# #

**Beschreibung**: Hiermit können Sie eine Schnittstelle mit vorhandenen Membern einer Klasse, Struktur oder Schnittstelle erstellen.

**Hintergrund**: Sie haben mehrere Klassen, Strukturen oder Schnittstellen mit Methoden, die allgemeingültig gestaltet und von anderen Klassen, Strukturen oder Schnittstellen verwendet werden könnten.

**Vorteile**: Schnittstellen stellen hervorragende Konstrukte für objektorientierte Entwürfe dar.  Stellen Sie sich vor, es gäbe Klassen für verschiedene Tiere (Hunde, Katzen, Vögel) mit häufig verwendeten Methoden wie Fressen, Trinken und Schlafen.  Mit einer Schnittstelle wie IAnimal würden Hunden, Katzen und Vögeln eine gemeinsame „Signatur“ für diese Methoden zugewiesen werden.

**Vorgehensweise**:

1. Markieren Sie den Namen der Klasse, für die die Aktion ausgeführt wird, oder platzieren Sie den Textcursor einfach an eine beliebige Stelle im Klassennamen.

   ![Markierter Code](media/extractinterface-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+R** und dann **STRG+I**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Schnittstelle extrahieren** aus.
   * **Maus**
     * Wählen Sie **Bearbeiten > Umgestalten > Schnittstelle extrahieren** aus.
     * Klicken Sie mit der rechten Maustaste auf den Namen der Klasse, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Schnittstelle extrahieren** aus.

1. Geben Sie im angezeigten Dialogfeld **Schnittstelle extrahieren** die erforderlichen Informationen ein: ![Schnittstelle extrahieren](media/extractinterface-dialog-cs.png)
   | Feld | description |
   | --- | --- |
   | **Name der neuen Schnittstelle** | Der Name der zu erstellenden Schnittstelle. Dies ist standardmäßig I*ClassName*, wobei *ClassName* der Name der von Ihnen oben ausgewählten Klasse ist. |
   | **Neuer Dateiname** | Der Name der generierten Datei, die die Schnittstelle enthält. Wie beim Namen der Schnittstelle ist dies standardmäßig I*ClassName*, wobei *ClassName* der Name der von Ihnen oben ausgewählten Klasse ist. |
   | **Öffentliche Member zum Bilden einer Schnittstelle auswählen** | Die in der Schnittstelle zu extrahierenden Elemente.  Sie können beliebig viele Elemente auswählen. |

1. Klicken Sie auf **OK**.

   Die Schnittstelle wird sofort in der Datei mit dem angegebenen Namen erstellt.  Darüber hinaus implementiert die ausgewählte Klasse nun diese Schnittstelle.

   ![Resultierende Klasse](media/extractinterface-class-cs.png)
   ![Resultierende Schnittstelle](media/extractinterface-interface-cs.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)