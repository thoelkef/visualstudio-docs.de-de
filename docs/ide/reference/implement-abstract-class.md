---
title: Implementieren einer abstrakten Klasse in Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6fc870e53e9323b8f76cfa39b2e6f961b04e973a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825763"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementieren einer abstrakten Klasse in Visual Studio

Diese Codegenerierung gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie sofort den für die Implementierung einer abstrakten Klasse erforderlichen Code generieren.

**Hintergrund**: Sie möchten von einer abstrakten Klasse erben.

**Vorteile**: Sie könnten nacheinander alle abstrakten Member manuell implementieren, doch bei diesem Feature werden alle Methodensignaturen automatisch generiert.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in die Zeile mit einer roten Wellenlinie, die darauf hinweist, dass Sie aus einer abstrakte Klasse geerbt, jedoch nicht alle erforderlichen Members implementiert haben.

   - C#:

       ![Hervorgehobener Code – C#](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code in Visual Basic](media/abstract-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
      - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
      - Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-cs.png) das angezeigt wird.
      - Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

   ![Vorschau der Aktion zum Implementieren einer Klasse](media/abstract-preview-cs.png)

3. Klicken Sie im Dropdownmenü auf **Abstrakte Klasse implementieren**.

   > [!TIP]
   > - Klicken Sie im unteren Bereich des Vorschaufensters auf den Link **Vorschau der Änderungen**, um vor einer Auswahl [alle Änderungen anzuzeigen](../../ide/preview-changes.md), die vorgenommen werden.
   > - Klicken Sie auf die Links **Dokument**, **Projekt** und **Projektmappe**, um die richtigen Methodensignaturen für verschiedene Klassen zu erstellen, die von der abstrakten Klasse erben.

   Die abstrakten Methodensignaturen werden erstellt und stehen für die Implementierung zur Verfügung.

   - C#:

       ![Ergebnis der Aktion zum Implementieren einer Klasse in C#](media/abstract-result-cs.png)

   - Visual Basic:

       ![Ergebnis der Aktion zum Implementieren einer Klasse in Visual Basic](media/abstract-result-vb.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)