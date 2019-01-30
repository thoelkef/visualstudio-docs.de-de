---
title: Generieren einer Methode
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c2de6f8608857d102454d03a98aacd175a22cef
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024941"
---
# <a name="generate-a-method-in-visual-studio"></a>Generieren einer Methode in Visual Studio

Diese Codegenerierung gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit können Sie sofort eine Methode zu einer Klasse hinzufügen.

**Hintergrund:** Sie führen eine neue Methode ein, die ordnungsgemäß automatisch deklariert werden soll.

**Vorteile**: Sie können die Methode und Parameter vor der Verwendung zwar deklarieren, bei diesem Feature wird die Deklaration jedoch automatisch generiert.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor auf der Zeile, in der eine rote Wellenlinie angezeigt wird. Die rote Wellenlinie weist auf eine Methode hin, die noch nicht vorhanden ist.

   - C#:

       ![Hervorgehobener Code – C#](media/method-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code in Visual Basic](media/method-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
      - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
      - Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-cs.png) das angezeigt wird.
      - Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert wurde.

      ![Vorschau der Aktion zum Generieren einer Methode](media/method-preview-cs.png)

3. Klicken Sie im Dropdownmenü auf **Methode generieren**.

   > [!TIP]
   > Klicken Sie im unteren Bereich des Vorschaufensters auf den Link **Vorschau der Änderungen**, um vor einer Auswahl [alle Änderungen anzuzeigen](../../ide/preview-changes.md), die vorgenommen werden.

   Die Methode wird mit Parametern erstellt, die aus der Verwendung abgeleitet werden.

   - C#:

       ![Ergebnis der Methodengenerierung in C#](media/method-result-cs.png)

   - Visual Basic:

       ![Ergebnis der Methodengenerierung in Visual Basic](media/method-result-vb.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)