---
title: Die Eigenschaft kann nicht gelöscht werden
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d12f974e1949bfb96cd2d6bb774eb2b73f371689
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Die Eigenschaft \<Eigenschaftsname > kann nicht gelöscht werden

Die Eigenschaft \<Eigenschaftsname > kann nicht gelöscht werden, da es als festgelegt ist die **Unterscheidungseigenschaft** für die Vererbung zwischen \<Klassenname > und \<Klassenname >

Die ausgewählte Eigenschaft wird festgelegt, wie die **Unterscheidungseigenschaft** für die Vererbung zwischen den Klassen angegeben, in der Fehlermeldung. Eigenschaften können nicht gelöscht werden, wenn sie zwischen Datenklassen an der Vererbungskonfiguration teilnehmen.

Legen Sie die **Unterscheidungseigenschaft** auf eine andere Eigenschaft der Datenklasse fest, die die gewünschte Eigenschaft gelöscht werden kann.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Wählen Sie im O/R-Designer die Vererbungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.

2. Legen Sie die **Unterscheidungseigenschaft** Eigenschaft auf eine andere Eigenschaft.

3. Versuchen Sie erneut, die Eigenschaft zu löschen.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)