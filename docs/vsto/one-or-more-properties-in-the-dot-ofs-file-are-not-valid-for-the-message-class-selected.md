---
title: Mindestens eine Eigenschaft in der OFS-Datei ist für die ausgewählte Nachrichtenklasse ungültig
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d58ad6ff89d8cf41ec60135cfbfe3deac1382f1e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977860"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Mindestens eine Eigenschaft in der OFS-Datei ist für die ausgewählte Nachrichtenklasse ungültig
  Dieser Fehler wird angezeigt, wenn Sie einen Formularbereich importieren, die in Outlook entworfen wurde, aber ein oder mehrere Felder im Formularbereich nicht kompatibel mit den Nachrichtenklassen, die Sie auf der letzten Seite des Auswählen der **neuer Formularbereich** Assistenten.

Beispielsweise können Sie **Aufgabe (IPM.Task)** auf der letzten Seite des Assistenten **Neuer Formularbereich** auswählen. Wenn der Formularbereich verfügt über eine **Geschäftsadresse** Feld, Sie erhalten diesen Fehler, da eine Aufgabe Geschäftsadresse besitzt. Aus diesem Grund die **Geschäftsadresse** Feld ist nicht kompatibel mit der `IPM.Task` message-Klasse.

 Sie können auswählen, **Aufgabe (IPM. Aufgabe)** auf der letzten Seite des der **neuer Formularbereich** Assistenten. Wenn der Formularbereich verfügt über eine **Geschäftsadresse** Feld, Sie erhalten diesen Fehler, da eine Aufgabe Geschäftsadresse besitzt. Aus diesem Grund die **Geschäftsadresse** Feld ist nicht kompatibel mit der `IPM.Task` message-Klasse.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Auf der letzten Seite des Assistenten **Neuer Formularbereich** wählen Sie eine Nachrichtenklasse aus, die mit den Feldern im Formularbereich kompatibel ist.

- Entfernen Sie im Formulardesigner in Outlook Felder, die nicht mit den Nachrichtenklassen kompatibel sind. Entfernen von Feldern, die Sie planen, wählen Sie auf der letzten Seite des der **neuer Formularbereich** Assistenten.

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Importieren Sie einen, der in Outlook entworfenen Formularbereich](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
