---
title: "Generieren Sie eine Außerkraftsetzung - Generierung von Code (Visual Basic) | Microsoft Docs"
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
ms.openlocfilehash: 4a384eb3e75a499eb2a35c747f003846580738e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="generate-an-override-in-visual-basic"></a>Generieren Sie eine Außerkraftsetzung in Visual Basic
**Was:** können Sie den Code für eine jede Methode überschrieben werden kann direkt von einer Basisklasse generieren. 

**Wann:** eine Methode der Basisklasse überschreiben und die Signatur automatisch generiert werden sollen.  

**Grund:** Sie konnte die Signatur der Methode selbst schreiben, aber diese Funktion die Signatur automatisch generiert. 

**Vorgehensweise:**

1. Typ der **überschreibt** -Schlüsselwort, gefolgt von einem Leerzeichen, in dem Sie eine Signatur außer Kraft gesetzte Methode einfügen möchten und eine IntelliSense-Dropdownliste wird angezeigt.

   ![Überschreiben von IntelliSense](media/override_intellisense.png)

1. Wählen Sie die Methode, die Sie von der Basisklasse zu überschreiben, indem Sie darauf klicken, mit der Maus, oder navigieren, mit der Tastatur drücken möchten **EINGABETASTE**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override_property.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override_method.png) to show or hide Methods in the list.
-->

1. Die ausgewählte Methode oder Eigenschaft wird auf die Klasse als eine Außerkraftsetzung, die implementiert werden können hinzugefügt werden.

   ![Überschreiben Sie Ergebnis](media/override_result.png)

## <a name="see-also"></a>Siehe auch  
[Codegenerierung (Visual Basic)](../code-generation-vb.md) 