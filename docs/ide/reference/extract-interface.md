---
title: Refactoring des Extrahierens einer Schnittstelle in Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b126d3753c0b4d92a3ef7bc2579c6208e61e308b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849880"
---
# <a name="extract-an-interface-refactoring"></a>Refactoring des Extrahierens einer Schnittstelle

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie eine Schnittstelle mit vorhandenen Membern einer Klasse, Struktur oder Schnittstelle erstellen.

**Hintergrund**: Sie haben mehrere Klassen, Strukturen oder Schnittstellen mit Methoden, die allgemeingültig gestaltet und von anderen Klassen, Strukturen oder Schnittstellen verwendet werden könnten.

**Vorteile**: Schnittstellen stellen hervorragende Konstrukte für objektorientierte Entwürfe dar. Stellen Sie sich vor, es gäbe Klassen für verschiedene Tiere (Hunde, Katzen, Vögel) mit häufig verwendeten Methoden wie Fressen, Trinken und Schlafen. Mit einer Schnittstelle wie IAnimal würden Hunden, Katzen und Vögeln eine gemeinsame „Signatur“ für diese Methoden zugewiesen werden.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den Namen der Klasse, für die die Aktion ausgeführt wird, oder platzieren Sie den Textcursor einfach an eine beliebige Stelle im Klassennamen.

   - C#:

       ![Hervorgehobener Code – C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code – Visual Basic](media/extractinterface-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie **STRG+R** und dann **STRG+I**. (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Schnittstelle extrahieren** aus.
   - **Maus**
      - Wählen Sie **Bearbeiten > Umgestalten > Schnittstelle extrahieren** aus.
      - Klicken Sie mit der rechten Maustaste auf den Namen der Klasse, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Schnittstelle extrahieren** aus.

3. Geben Sie im angezeigten Dialogfeld **Schnittstelle extrahieren** die erforderlichen Informationen ein:

   ![Schnittstelle extrahieren](media/extractinterface-dialog-cs.png)


   | Feld | Beschreibung  |
   | - | - |
   | **Name der neuen Schnittstelle** | Der Name der zu erstellenden Schnittstelle. Dies ist standardmäßig I*ClassName*, wobei *ClassName* der Name der von Ihnen oben ausgewählten Klasse ist. |
   | **Neuer Dateiname** | Der Name der generierten Datei, die die Schnittstelle enthält. Wie beim Namen der Schnittstelle ist dies standardmäßig I*ClassName*, wobei *ClassName* der Name der von Ihnen oben ausgewählten Klasse ist. |
   | **Öffentliche Member zum Bilden einer Schnittstelle auswählen** | Die in der Schnittstelle zu extrahierenden Elemente. Sie können beliebig viele Elemente auswählen. |


4. Klicken Sie auf **OK**.

   Die Schnittstelle wird in der Datei mit dem angegebenen Namen erstellt. Darüber hinaus implementiert die ausgewählte Klasse diese Schnittstelle.

   - C#:

      ![Sich ergebende Klasse – C#](media/extractinterface-class-cs.png) ![Sich ergebende Schnittstelle – C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Sich ergebende Klasse – Visual Basic](media/extractinterface-class-vb.png) ![Sich ergebende Schnittstelle – Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)