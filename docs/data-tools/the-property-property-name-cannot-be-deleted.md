---
title: Die Eigenschaft kann nicht gelöscht werden
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7e85860de7494ae7d93ad37bd0a115fa786f0a87
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174012"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Die Eigenschaft \<Eigenschaftenname > kann nicht gelöscht werden

Die Eigenschaft \<Eigenschaftenname > kann nicht gelöscht werden, da es sich handelt die **Unterscheidungseigenschaft** für die Vererbung zwischen \<Klassenname > und \<Klassenname >

Die ausgewählte Eigenschaft wird festgelegt, als die **Unterscheidungseigenschaft** für die Vererbung zwischen den Klassen, die in der Fehlermeldung angegeben. Eigenschaften können nicht gelöscht werden, wenn sie zwischen Datenklassen an der Vererbungskonfiguration teilnehmen.

Legen Sie die **Unterscheidungseigenschaft** auf eine andere Eigenschaft der Datenklasse fest, damit die gewünschte Eigenschaft gelöscht werden kann.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. In der **O/R Designer**, wählen Sie die Vererbungslinie aus, die die Datenklassen verbindet in der Fehlermeldung angegeben.

2. Legen Sie die **Diskriminator** Eigenschaft auf eine andere Eigenschaft.

3. Versuchen Sie erneut, die Eigenschaft zu löschen.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)