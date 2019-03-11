---
title: Refactoring des Extrahierens einer Schnittstelle
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f0036bb9bf8ef6d0c09fddc2b8ac0a4977c3674c
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323431"
---
# <a name="extract-an-interface-refactoring"></a>Refactoring des Extrahierens einer Schnittstelle

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit können Sie eine Schnittstelle mit vorhandenen Membern einer Klasse, Struktur oder Schnittstelle erstellen.

**Hintergrund:** Sie haben Member in einer Klasse, Struktur oder Schnittstelle, die von anderen Klassen, Strukturen oder Schnittstellen geerbt werden können.

**Vorteile**: Schnittstellen stellen hervorragende Konstrukte für objektorientierte Entwürfe dar. Stellen Sie sich vor, es gäbe Klassen für verschiedene Tiere (Hunde, Katzen, Vögel) mit häufig verwendeten Methoden wie Fressen, Trinken und Schlafen. Mit einer Schnittstelle wie IAnimal würden Hunden, Katzen und Vögeln eine gemeinsame „Signatur“ für diese Methoden zugewiesen werden.

## <a name="extract-an-interface-refactoring"></a>Refactoring des Extrahierens einer Schnittstelle

1. Platzieren Sie Ihren Cursor auf dem Klassenname.

   - C#:

       ![Hervorgehobener Code – C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code – Visual Basic](media/extractinterface-highlight-vb.png)

2. Führen Sie anschließend eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie **STRG+R** und dann **STRG+I**. (Ihre Tastenkombination weicht je nach dem gewählten Profil möglicherweise ab.)
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Schnittstelle extrahieren** aus.
   - **Maus**
      - Wählen Sie **Bearbeiten > Umgestalten > Schnittstelle extrahieren** aus.
      - Klicken Sie mit der rechten Maustaste auf den Namen der Klasse, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Schnittstelle extrahieren** aus.

3. Geben Sie im angezeigten Dialogfeld **Schnittstelle extrahieren** die erforderlichen Informationen ein:

   ![Schnittstelle extrahieren](media/extractinterface-dialog-same-file.png)


   | Feld | Beschreibung |
   | - | - |
   | **Name der neuen Schnittstelle** | Der Name der zu erstellenden Schnittstelle. Dieser Name ist standardmäßig I*ClassName*, wobei *ClassName* der Name der von Ihnen oben ausgewählten Klasse ist. |
   | **Neuer Dateiname** | Der Name der generierten Datei, die die Schnittstelle enthalten wird. Wie beim Namen der Schnittstelle ist dies standardmäßig I*ClassName*, wobei *ClassName* der Name der von Ihnen oben ausgewählten Klasse ist. Sie können für die Option auch **Add to current file** (Aktueller Datei hinzufügen) auswählen. |
   | **Öffentliche Member zum Bilden einer Schnittstelle auswählen** | Die in der Schnittstelle zu extrahierenden Elemente. Sie können beliebig viele Elemente auswählen. |


4. Klicken Sie auf **OK**.

   Die Schnittstelle wird in der Datei mit dem angegebenen Namen erstellt. Darüber hinaus implementiert die ausgewählte Klasse diese Schnittstelle.

   - C#:

      ![Sich ergebende Klasse – C#](media/extractinterface-class-cs.png) ![Sich ergebende Schnittstelle – C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Sich ergebende Klasse – Visual Basic](media/extractinterface-class-vb.png) ![Sich ergebende Schnittstelle – Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../../ide/visual-studio-2017-for-dotnet-developers.md)