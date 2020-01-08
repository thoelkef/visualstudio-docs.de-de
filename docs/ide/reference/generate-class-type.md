---
title: Generieren einer Klasse oder eines Typs
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 94786ef10e427a0deb4f80471305509124f1638b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595630"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generieren einer Klasse oder eines Typs in Visual Studio

Diese Codegenerierung gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit können Sie sofort den Code für eine Klasse oder einen Typ generieren.

**Hintergrund:** Sie führen eine neue Klasse oder einen neuen Typ ein, die bzw. der ordnungsgemäß automatisch deklariert werden soll.

**Vorteile**: Sie können die Klasse oder den Typ vor der Verwendung zwar deklarieren, bei diesem Feature wird die Klasse bzw. der Typ jedoch automatisch generiert.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor auf der Zeile, in der eine rote Wellenlinie angezeigt wird. Die rote Wellenlinie weist auf eine Klasse hin, die noch nicht vorhanden ist.

   - C#:

       ![Hervorgehobener Code – C#](media/class-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code in Visual Basic](media/class-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
      - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
      - Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Fehlerglühbirnensymbol](media/error-bulb.png) das angezeigt wird.
      - Klicken Sie auf die Schaltfläche ![Fehlerglühbirnensymbol](media/error-bulb.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert wurde.

      ![Vorschau der Aktion „Klasse generieren“](media/class-preview-cs.png)

3. Wählen Sie im Dropdownmenü eine der folgenden Optionen aus:

   - Klasse „*TypeName*“ in neuer Datei generieren &mdash; Erstellt eine Klasse mit dem Namen *TypeName* in einer Datei namens *TypeName*.cs/.vb.
   - Klasse „*TypeName*“ generieren &mdash; Erstellt eine Klasse mit dem Namen *TypeName* in der aktuellen Datei.
   - Geschachtelte Klasse „*TypeName*“ generieren &mdash; Erstellt eine Klasse mit dem Namen *TypeName* in der aktuellen Klasse.
   - Neuen Typ generieren... &mdash; Erstellt eine neue Klasse oder Struktur mit allen von Ihnen angegebenen Eigenschaften.

   > [!TIP]
   > Klicken Sie im unteren Bereich des Vorschaufensters auf den Link **Vorschau der Änderungen**, um vor einer Auswahl [alle Änderungen anzuzeigen](../../ide/preview-changes.md), die vorgenommen werden.

4. Wenn Sie das Element **Neuen Typ generieren** ausgewählt haben, wird das Dialogfeld **Typ generieren** geöffnet. Konfigurieren Sie den Zugriff, die Art und den Speicherort des neuen Typs.

   ![Typ generieren](media/class-newtype-cs.png)

   Auswahl | Beschreibung
   --- | ---
   Zugriff | Legen Sie den Zugriffstyp auf *Standard*, *Intern* oder *Öffentlich* fest.
   Art | Dieses Element kann auf *Klasse* oder *Struktur* festgelegt werden.
   name | Dies ist der Name, den Sie bereits eingegeben haben, und kann nicht geändert werden.
   Projekt | Wenn mehrere Projekte in Ihrer Projektmappe vorhanden sind, können Sie festlegen, in welchem Projekt die Klasse bzw. Struktur verwendet werden soll.
   Dateiname | Sie können eine neue Datei erstellen oder den Typ zu einer vorhandenen Datei hinzufügen.

Die Klasse oder die Struktur wird erstellt. Für C# wird auch ein Konstruktor erstellt.

- C#

   ![Ergebnis der Generierung einer Klasse in C#](media/class-result-cs.png)

- Visual Basic

   ![Ergebnis der Generierung einer Klasse in Visual Basic](media/class-result-vb.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
