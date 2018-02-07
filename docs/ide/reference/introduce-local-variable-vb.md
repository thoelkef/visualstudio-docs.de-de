---
title: "Bereitstellen einer lokalen Variable – Codegenerierung (Visual Basic) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: abc0ef3ffdbada86a66bac9823894ee83d04047f
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2018
---
# <a name="introduce-a-local-variable-in-visual-basic"></a>Bereitstellen einer lokalen Variable in Visual Basic
**Beschreibung**: Hiermit können Sie sofort eine lokale Variable generieren, um einen vorhandenen Ausdruck zu ersetzen.

**Hintergrund**: Sie verwenden einen Code, der bei Verwendung in einer lokalen Variable später problemlos wiederverwendet werden kann.  

**Vorteile**: Sie könnten den Code für die Verwendung an verschiedenen Stellen mehrmals kopieren und einfügen. Besser wäre es jedoch, den Vorgang einmal durchzuführen, das Ergebnis in einer lokalen Variable zu speichern und durchgehend die lokale Variable zu verwenden. 

**Vorgehensweise**:

1. Markieren Sie den Ausdruck, der einer neuen lokalen Variable zugewiesen werden soll.

   ![Markierter Code](media/local-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Lokales Element für alle Vorkommen von "*Ausdruck*" bereitstellen** aus, wobei *Ausdruck* für den von Ihnen markierten Code steht.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus. Wählen Sie dann im Vorschaupopupfenster **Lokales Element für alle Vorkommen von "*Ausdruck*" bereitstellen** aus, wobei *Ausdruck* für den markierten Code steht.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-vb.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

   ![Vorschau der Aktion zum Bereitstellen eines lokalen Elements](media/local-preview-vb.png)

   >[!TIP]
   >Klicken Sie im unteren Bereich des Vorschaufensters auf den Link [**Vorschau der Änderungen**](../../ide/preview-changes.md), um vor einer Auswahl alle Änderungen anzuzeigen, die vorgenommen werden.

1. Die lokale Variable wird automatisch mit dem aus der Verwendung abgeleiteten Typ erstellt.  Geben Sie einen Namen für die neue lokale Variable ein.

   ![Ergebnis der Aktion zum Bereitstellen eines lokalen Elements](media/local-result-vb.png)

   >[!NOTE]
   >Sie können die Menüoption **...alle Vorkommen von...** verwenden, um nicht nur den speziell markierten Ausdruck zu ersetzen, sondern jede Instanz des gefundenen markierten Ausdrucks.

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md) 