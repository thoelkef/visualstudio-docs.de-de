---
title: "Generieren einer Überschreibung – Codegenerierung (C#) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 3801d8ce60cf87126f8894bf44c77056f996cde1
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2018
---
# <a name="generate-an-override-in-c"></a>Generieren einer Überschreibung in C# #

**Beschreibung**: Sie können sofort Code für eine Methode generieren, die von einer Basisklasse überschrieben werden kann.

**Hintergrund**: Sie möchten eine Basisklassenmethode überschreiben und die Signatur automatisch generieren.

**Vorteile**: Sie könnten die Methodensignatur selbst schreiben – dieses Feature generiert die Signatur jedoch automatisch.

**Vorgehensweise**:

1. Geben Sie an der Position, an der Sie eine überschriebene Methodensignatur einfügen möchten, das Schlüsselwort **override** ein, gefolgt von einem Leerzeichen. Es wird eine IntelliSense-Dropdownliste angezeigt.

   ![Überschreiben mit IntelliSense](media/override-intellisense-cs.png)

1. Wählen Sie aus der Basisklasse die Methode aus, die Sie überschreiben möchten, indem Sie mit der Maus auf die Methode klicken oder mit der Tastatur dorthin navigieren und die **EINGABETASTE** drücken.

   >[!TIP]
   >* Verwenden Sie das Eigenschaftssymbol, ![Eigenschaftssymbol](media/override-property-cs.png) um Eigenschaften in der Liste anzuzeigen oder auszublenden.
   >* Verwenden Sie das Methodensymbol, ![Methodensymbol](media/override-method-cs.png) um Methoden in der Liste anzuzeigen oder auszublenden.

1. Die ausgewählte Methode oder Eigenschaft wird der Klasse als Überschreibung hinzugefügt und steht für die Implementierung zur Verfügung.

   ![Ergebnis der Überschreibung](media/override-result-cs.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)
