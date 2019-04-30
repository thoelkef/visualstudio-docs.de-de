---
title: Die Eigenschaft kann nicht gelöscht werden
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4b1e0652d19b10b1d1ede7b1b950d89ca1bf670c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565432"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Die \<Eigenschaftenname>-Eigenschaft kann nicht gelöscht werden

Die \<Eigenschaftenname>-Eigenschaft kann nicht gelöscht werden, da sie als **Diskriminatoreigenschaft** für die Vererbung zwischen \<Klassenname> und \<Klassenname> festgelegt ist.

Die ausgewählte Eigenschaft wird als **Diskriminatoreigenschaft** für die Vererbung zwischen den in der Fehlermeldung angegebenen Klassen festgelegt. Eigenschaften können nicht gelöscht werden, wenn sie zwischen Datenklassen an der Vererbungskonfiguration teilnehmen.

Legen Sie die **Diskriminatoreigenschaft** auf eine andere Eigenschaft der Datenklasse fest, damit die gewünschte Eigenschaft gelöscht werden kann.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Wählen Sie im **O/R-Designer** die Vererbungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.

2. Legen Sie die **Diskriminatoreigenschaft** auf eine andere Eigenschaft fest.

3. Versuchen Sie erneut, die Eigenschaft zu löschen.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)