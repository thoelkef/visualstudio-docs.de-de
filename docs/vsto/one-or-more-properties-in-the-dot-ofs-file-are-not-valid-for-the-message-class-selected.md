---
title: Mindestens eine Eigenschaft in der OFS-Datei ist für die ausgewählte Nachrichtenklasse ungültig
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
ms.openlocfilehash: cfae8533337bbe18c89dbb670fb58a0c89c6c54c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692498"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Mindestens eine Eigenschaft in der OFS-Datei ist für die ausgewählte Nachrichtenklasse ungültig
  Dieser Fehler wird angezeigt, wenn Sie einen Formularbereich importieren, die in Outlook entworfen wurde, aber ein oder mehrere Felder im Formularbereich nicht kompatibel mit den Nachrichtenklassen, die Sie auf der letzten Seite des Auswählen der **neuer Formularbereich** Assistenten.  

Beispielsweise können Sie **Aufgabe (IPM.Task)** auf der letzten Seite des Assistenten **Neuer Formularbereich** auswählen. Wenn die Formularbereich verfügt eine **Geschäftsadresse** Feld, Sie erhalten diesen Fehler, da eine Aufgabe eine Geschäftsadresse besitzt. Aus diesem Grund die **Geschäftsadresse** Feld ist nicht kompatibel mit der `IPM.Task` message-Klasse.  
  
 Sie können Sie wählen, **Aufgabe (IPM. Aufgabe)** auf der letzten Seite des der **neuer Formularbereich** Assistenten. Wenn die Formularbereich verfügt eine **Geschäftsadresse** Feld, Sie erhalten diesen Fehler, da eine Aufgabe eine Geschäftsadresse besitzt. Aus diesem Grund die **Geschäftsadresse** Feld ist nicht kompatibel mit der `IPM.Task` message-Klasse.  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Auf der letzten Seite des Assistenten **Neuer Formularbereich** wählen Sie eine Nachrichtenklasse aus, die mit den Feldern im Formularbereich kompatibel ist.  
  
-   Entfernen Sie im Formulardesigner in Outlook Felder, die nicht mit den Nachrichtenklassen kompatibel sind. Entfernen von Feldern, die Sie auswählen, klicken Sie auf der letzten Seite des möchten der **neuer Formularbereich** Assistenten.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Importieren eines, das in Outlook entworfenen Formularbereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  