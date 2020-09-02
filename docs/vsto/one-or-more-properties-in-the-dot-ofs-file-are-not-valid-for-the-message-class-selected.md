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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977860"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Mindestens eine Eigenschaft in der OFS-Datei ist für die ausgewählte Nachrichtenklasse ungültig
  Dieser Fehler wird angezeigt, wenn Sie einen Formular Bereich importieren, der in Outlook entworfen wurde, aber ein oder mehrere Felder im Formular Bereich nicht mit den Nachrichten Klassen kompatibel sind, die Sie auf der letzten Seite des Assistenten **neuer Formular Bereich** auswählen.

Beispielsweise können Sie **Aufgabe (IPM.Task)** auf der letzten Seite des Assistenten **Neuer Formularbereich** auswählen. Wenn der Formular Bereich ein Feld für die **Geschäftsadresse** enthält, wird dieser Fehler angezeigt, da eine Aufgabe nicht über eine geschäftliche Adresse verfügt. Aus diesem Grund ist das Feld **Geschäftsadresse** nicht mit der `IPM.Task` Message-Klasse kompatibel.

 Möglicherweise Wählen Sie **Aufgabe (IPM). Aufgabe)** auf der letzten Seite des Assistenten **neuer Formular Bereich** . Wenn der Formular Bereich ein Feld für die **Geschäftsadresse** enthält, wird dieser Fehler angezeigt, da eine Aufgabe nicht über eine geschäftliche Adresse verfügt. Aus diesem Grund ist das Feld **Geschäftsadresse** nicht mit der `IPM.Task` Message-Klasse kompatibel.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Auf der letzten Seite des Assistenten **Neuer Formularbereich** wählen Sie eine Nachrichtenklasse aus, die mit den Feldern im Formularbereich kompatibel ist.

- Entfernen Sie im Forms-Designer in Outlook Felder, die nicht mit den Nachrichten Klassen kompatibel sind. Entfernen Sie die Felder, die Sie auswählen möchten, auf der letzten Seite des Assistenten **neuer Formular Bereich** .

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formular Bereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
