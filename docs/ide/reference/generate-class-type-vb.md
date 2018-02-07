---
title: "Generieren einer Klasse oder eines Typs – Codegenerierung (Visual Basic) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4a4ff45a59fb53964a365f31cc4d5f48a5b159dc
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-class-or-type-in-visual-basic"></a>Generieren einer Klasse oder eines Typs in Visual Basic
**Beschreibung**: Hiermit können Sie sofort den Code für eine Klasse oder einen Typ generieren. 

**Hintergrund**: Sie führen eine neue Klasse oder einen neuen Typ ein, die bzw. der ordnungsgemäß automatisch deklariert werden soll.  

**Vorteile**: Sie können die Klasse oder den Typ vor der Verwendung zwar deklarieren, bei diesem Feature wird die Klasse bzw. der Typ jedoch automatisch generiert. 

**Vorgehensweise**:

1. Platzieren Sie den Cursor in die Zeile mit einer roten Wellenlinie, die darauf hinweist, dass Sie eine noch nicht vorhandene Klasse verwendet haben.

   ![Markierter Code](media/class-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie eine der Optionen aus dem Popupvorschaufenster aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie eine der Optionen aus dem Popupvorschaufenster aus.
     * Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-vb.png) das angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-vb.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

   ![Vorschau der Aktion „Klasse generieren“](media/class-preview-vb.png)

   Auswahl | description
   --- | ---
   Klasse „*TypeName*“ in neuer Datei generieren | Erstellt eine Klasse mit dem Namen *TypeName* in einer Datei namens „*TypeName*.cs/.vb“.
   Klasse „*TypeName*“ generieren | Erstellt eine Klasse mit dem Namen *TypeName* in der aktuellen Datei.
   Geschachtelte Klasse „*TypeName*“ generieren | Erstellt eine Klasse mit dem Namen *TypeName* in der aktuellen Klasse.
   Neuen Typ generieren... | Erstellt eine neue Klasse oder Struktur mit allen von Ihnen angegebenen Eigenschaften.

   >[!TIP]
   >Klicken Sie im unteren Bereich des Vorschaufensters auf den Link [**Vorschau der Änderungen**](../../ide/preview-changes.md), um vor einer Auswahl alle Änderungen anzuzeigen, die vorgenommen werden.

1. Bei Auswahl des Elements **Neuen Typ generieren...** wird ein Dialogfeld angezeigt, mit dem Sie einige zusätzliche Aktionen durchführen können.

   ![Typ generieren](media/class-newtype-vb.png)

   Auswahl | description
   --- | ---
   Zugriff | Legen Sie den Zugriffstyp auf *Standard*, *Intern* oder *Öffentlich* fest.
   Art | Dieses Element kann auf *Klasse* oder *Struktur* festgelegt werden.
   name | Dies ist der Name, den Sie bereits eingegeben haben, und kann nicht geändert werden.
   Projekt | Wenn mehrere Projekte in Ihrer Projektmappe vorhanden sind, können Sie festlegen, in welchem Projekt die Klasse bzw. Struktur verwendet werden soll.
   Dateiname | Sie können eine neue Datei erstellen oder den Typ zu einer vorhandenen Datei hinzufügen.

1. Die Klasse bzw. Struktur wird automatisch mit dem aus der Verwendung abgeleiteten Konstruktor erstellt.

   ![Ergebnis der Aktion zum Generieren einer Klasse](media/class-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)