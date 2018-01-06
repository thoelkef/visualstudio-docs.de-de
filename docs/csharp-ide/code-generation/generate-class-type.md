---
title: Erstellen Sie eine Klasse oder ein Typ - Generierung von Code (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: c72b9e898bd150e0d4ec1cc6a7a91d1eb7e6b7a8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-class-or-type-in-c"></a>Generieren Sie eine Klasse oder ein Typ in c# #
**Was:** können Sie sofort den Code für eine Klasse oder einen Typ zu generieren. 

**Wann:** einführen einer neuen Klasse oder den Typ und ordnungsgemäß, automatisch deklarieren möchten.  

**Grund:** konnten Sie die Klasse oder einen Typ deklarieren, vor der Verwendung, aber diese Funktion wird die Klasse generieren oder automatisch. 

**Vorgehensweise:**

1. Platzieren Sie den Cursor in der Zeile, in dem es eine rote Wellenlinie, der angibt, Sie verwendet haben, eine Klasse, die noch nicht vorhanden ist.

   ![Hervorgehobene code](media/class_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü, und wählen Sie eine der Optionen im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** Menü, und wählen Sie eine der Optionen im Popupmenü Fenster Vorschau.
     * Die rote Wellenlinie zeigen, und klicken Sie auf der ![Glühbirne](media/bulb.png) Symbol "angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor bereits in der Zeile mit die rote Wellenlinie vorhanden ist.

   ![Vorschau der Klasse generieren](media/class_preview.png)

   Auswahl | Beschreibung
   --- | ---
   Klasse generieren*TypeName*"in der neuen Datei | Erstellt eine Klasse mit dem Namen *TypeName* in einer Datei namens *TypeName*cs/vb
   Klasse generieren*TypeName*" | Erstellt eine Klasse mit dem Namen *TypeName* in der aktuellen Datei.
   Generieren Sie eine geschachtelte Klasse*TypeName*" | Erstellt eine Klasse mit dem Namen *TypeName* in der aktuellen Klasse geschachtelt.
   Generieren Sie neuen Typ... | Erstellt eine neue Klasse oder Struktur mit allen Eigenschaften, die Sie angeben.

   >[!TIP]
   >Verwenden der [ **Vorschau der Änderungen** ](../../ide/preview-changes.md) Link am unteren Rand des Vorschaufensters, um alle Änderungen anzuzeigen, die vorgenommen wird, bevor Sie Ihre Auswahl getroffen haben.

1. Bei Auswahl der **neuen Typ generieren...**  Element, ein Dialogfeld wird angezeigt, die Sie einige zusätzlichen Aktionen durchführen können.

   ![Generieren von Typ](media/class_newtype.png)

   Auswahl | Beschreibung
   --- | ---
   Zugriff | Legen Sie den Typ haben *Standard*, *intern* oder *öffentlichen* Zugriff.
   Art | Dies kann festgelegt werden, als *Klasse* oder *Struktur*.
   name | Dies kann nicht geändert werden und werden der Name, den Sie bereits eingegeben haben.
   Projekt | Wenn mehrere Projekte in der Projektmappe vorhanden sind, können Sie auswählen, in dem die Klasse/Struktur Gültigkeitsdauer werden soll.
   Dateiname | Sie können eine neue Datei erstellen, oder Sie können den Typ hinzufügen, zu einer vorhandenen Datei.

1. Die Klasse/Struktur wird automatisch mit dem Konstruktor, der aus der Verwendung abgeleitet erstellt werden.

   ![Klasse Ergebnis generieren](media/class_result.png)

## <a name="see-also"></a>Siehe auch  
[Codegenerierung (C#)](../code-generation-csharp.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)