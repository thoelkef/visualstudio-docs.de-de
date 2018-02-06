---
title: "Generieren einer Überschreibung – Codegenerierung (Visual Basic) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 334f5a79dad1b7d2c14768d0698797a34ad039c5
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="generate-an-override-in-visual-basic"></a>Generieren einer Überschreibung in Visual Basic
**Zweck:** Sie können sofort Code für eine Methode generieren, die von einer Basisklasse überschrieben werden kann. 

**Hintergrund**: Sie möchten eine Basisklassenmethode überschreiben und die Signatur automatisch generieren.  

**Vorteile**: Sie könnten die Methodensignatur selbst schreiben – dieses Feature generiert die Signatur jedoch automatisch. 

**Vorgehensweise**:

1. Geben Sie an der Position, an der Sie eine überschriebene Methodensignatur einfügen möchten, das Schlüsselwort **Overrides** ein, gefolgt von einem Leerzeichen. Es wird eine IntelliSense-Dropdownliste angezeigt.

   ![Überschreiben mit IntelliSense](media/override-intellisense-vb.png)

1. Wählen Sie aus der Basisklasse die Methode aus, die Sie überschreiben möchten, indem Sie mit der Maus auf die Methode klicken oder mit der Tastatur dorthin navigieren und die **EINGABETASTE** drücken.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override-property-vb.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override-method-vb.png) to show or hide Methods in the list.
-->

1. Die ausgewählte Methode oder Eigenschaft wird der Klasse als Überschreibung hinzugefügt und steht für die Implementierung zur Verfügung.

   ![Ergebnis der Überschreibung](media/override-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md) 