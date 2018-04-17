---
title: Eine oder mehrere Eigenschaften in der OFS-Datei sind nicht für die ausgewählte Nachrichtenklasse ungültig | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ac9f5ab05ba6ed858946b5f665d850eea51c230
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Mindestens eine Eigenschaft in der OFS-Datei ist für die ausgewählte Nachrichtenklasse ungültig
  Dieser Fehler wird angezeigt, wenn Sie einen Formularbereich importieren, der in Outlook entworfen wurde, aber ein oder mehrere Felder im Formularbereich enthält, die mit den „message“-Klassen nicht kompatibel sind, die Sie auf der letzten Seite des Assistenten **Neuer Formularbereich** auswählen.  
  
 Beispielsweise können Sie **Aufgabe (IPM.Task)** auf der letzten Seite des Assistenten **Neuer Formularbereich** auswählen. Wenn der Formularbereich ein Feld für die **Geschäftsadresse** enthält, wird dieser Fehler angezeigt, da eine Aufgabe keine Geschäftsadresse besitzt. Aus diesem Grund ist das Feld **Geschäftsadresse** nicht mit der „IPM.Task“-Nachrichtenklasse kompatibel.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Auf der letzten Seite des Assistenten **Neuer Formularbereich** wählen Sie eine Nachrichtenklasse aus, die mit den Feldern im Formularbereich kompatibel ist.  
  
-   Entfernen Sie im Formulardesigner in Outlook Felder, die nicht mit den Nachrichtenklassen kompatibel sind, die Sie planen, auf der letzten Seite des Assistenten **Neuer Formularbereich** auszuwählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formularbereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  