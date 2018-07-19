---
title: Die Eigenschaft kann nicht gelöscht werden, da sie in der Zuordnung teilnimmt
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6ed6b14f64d16d1f18d4b358761169c3d424cee8
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174061"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Die Eigenschaft &lt;Eigenschaftennamen&gt; kann nicht gelöscht werden, da sie in der Zuordnung teilnimmt &lt;Zuordnungsname&gt;

Die ausgewählte Eigenschaft wird festgelegt, als die **Zuordnungseigenschaft** für die Zuordnung zwischen den Klassen, die in der Fehlermeldung angegeben. Eigenschaften können nicht gelöscht werden, wenn sie an einer Zuordnung zwischen Datenklassen beteiligt sind.

Legen Sie die **Zuordnungseigenschaft** auf eine andere Eigenschaft der Datenklasse fest, damit die gewünschte Eigenschaft gelöscht werden kann.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Wählen Sie auf die Assoziationslinie der **O/R Designer** , die in der Fehlermeldung angegebenen Datenklassen verbindet.

2. Doppelklicken Sie auf die Zeile zum Öffnen der **Zuordnungs-Editor** Dialogfeld.

3. Entfernen Sie die Eigenschaft aus der **Zuordnungseigenschaften**.

4. Versuchen Sie erneut, die Eigenschaft zu löschen.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)