---
title: Der Eigenschaften &lt; Name der Eigenschaft &gt; kann nicht gelöscht werden | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aca36919cb4c82d6ca76e0f3eecbbacd48cde768
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667244"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Der Eigenschaften &lt; Name der Eigenschaft &gt; kann nicht gelöscht werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Eigenschaft \<property name> kann nicht gelöscht werden, da Sie als diskriminatoreigenschaft für die Vererbung zwischen und festgelegt ist. \<class name>\<class name>

 Die ausgewählte Eigenschaft wird als **Diskriminatoreigenschaft** für die Vererbung zwischen den in der Fehlermeldung angegebenen Klassen festgelegt. Eigenschaften können nicht gelöscht werden, wenn sie zwischen Datenklassen an der Vererbungskonfiguration teilnehmen.

 Legen Sie die **Diskriminatoreigenschaft** auf eine andere Eigenschaft der Datenklasse fest, damit die gewünschte Eigenschaft gelöscht werden kann.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Wählen Sie im O/R-Designer die Vererbungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.

2. Legen Sie die **Diskriminatoreigenschaft** auf eine andere Eigenschaft fest.

3. Versuchen Sie erneut, die Eigenschaft zu löschen.

## <a name="see-also"></a>Weitere Informationen
 Vorgehens [Weise: Konfigurieren der Vererbung mithilfe des o/r-Designers](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) [Daten Klassen Vererbung (o/r-Designer)](../data-tools/data-class-inheritance-o-r-designer.md) Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen mithilfe einer Vererbung für eine einzelne Tabelle (o/r-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
