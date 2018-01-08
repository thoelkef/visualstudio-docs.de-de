---
title: "Eine oder mehrere Eigenschaften in der OFS-Datei sind nicht für die ausgewählte Nachrichtenklasse ungültig | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
ms.assetid: ca9e2ec1-df96-45ca-9611-cec47edfe1e4
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ca816a635abf929f2bfa1614f4560f434adbfd45
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Mindestens eine Eigenschaft in der OFS-Datei ist für die ausgewählte Nachrichtenklasse ungültig
  Dieser Fehler wird angezeigt, wenn Sie einen Formularbereich importieren, der in Outlook entworfen wurde, aber ein oder mehrere Felder im Formularbereich enthält, die mit den „message“-Klassen nicht kompatibel sind, die Sie auf der letzten Seite des Assistenten **Neuer Formularbereich** auswählen.  
  
 Beispielsweise können Sie **Aufgabe (IPM.Task)** auf der letzten Seite des Assistenten **Neuer Formularbereich** auswählen. Wenn der Formularbereich ein Feld für die **Geschäftsadresse** enthält, wird dieser Fehler angezeigt, da eine Aufgabe keine Geschäftsadresse besitzt. Aus diesem Grund ist das Feld **Geschäftsadresse** nicht mit der „IPM.Task“-Nachrichtenklasse kompatibel.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Auf der letzten Seite des Assistenten **Neuer Formularbereich** wählen Sie eine Nachrichtenklasse aus, die mit den Feldern im Formularbereich kompatibel ist.  
  
-   Entfernen Sie im Formulardesigner in Outlook Felder, die nicht mit den Nachrichtenklassen kompatibel sind, die Sie planen, auf der letzten Seite des Assistenten **Neuer Formularbereich** auszuwählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formularbereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  