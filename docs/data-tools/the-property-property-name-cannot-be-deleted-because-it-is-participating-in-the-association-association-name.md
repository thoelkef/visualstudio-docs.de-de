---
title: Die Eigenschaft kann nicht gelöscht werden, da diese in der Zuordnung beteiligt ist
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9e65049ae881ff11cd647fe09df3a6919dd8818c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Die Eigenschaft &lt;Eigenschaftsname&gt; kann nicht gelöscht werden, da sie in der Zuordnung teilnimmt &lt;Zuordnungsname&gt;

Die ausgewählte Eigenschaft wird festgelegt, wie die **Zuordnungseigenschaft** für die Zuordnung zwischen den Klassen angegeben, in der Fehlermeldung. Eigenschaften können nicht gelöscht werden, wenn sie an einer Zuordnung zwischen Datenklassen beteiligt sind.

Legen Sie die **Zuordnungseigenschaft** auf eine andere Eigenschaft der Datenklasse fest, die die gewünschte Eigenschaft gelöscht werden kann.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Wählen Sie im O/R-Designer die Zuordnungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.

2. Doppelklicken Sie auf die Zeile zum Öffnen der **Zuordnungs-Editor** (Dialogfeld).

3. Entfernen Sie die Eigenschaft aus der **Zuordnungseigenschaften**.

4. Versuchen Sie erneut, die Eigenschaft zu löschen.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)