---
title: Die Eigenschaft &lt;Eigenschaftennamen&gt; kann nicht gelöscht werden | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a212250791ececddbf2227d67d1f4652dc7de466
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661206"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Die Eigenschaft &lt;Eigenschaftennamen&gt; kann nicht gelöscht werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Eigenschaft \<Eigenschaftenname > kann nicht gelöscht werden, da sie als Unterscheidungseigenschaft für die Vererbung zwischen festgelegt ist \<Klassenname > und \<Klassenname >  
  
 Die ausgewählte Eigenschaft wird als **Diskriminatoreigenschaft** für die Vererbung zwischen den in der Fehlermeldung angegebenen Klassen festgelegt. Eigenschaften können nicht gelöscht werden, wenn sie zwischen Datenklassen an der Vererbungskonfiguration teilnehmen.  
  
 Legen Sie die **Diskriminatoreigenschaft** auf eine andere Eigenschaft der Datenklasse fest, damit die gewünschte Eigenschaft gelöscht werden kann.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Wählen Sie im O/R-Designer die Vererbungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.  
  
2.  Legen Sie die **Diskriminatoreigenschaft** auf eine andere Eigenschaft fest.  
  
3.  Versuchen Sie erneut, die Eigenschaft zu löschen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Datenklassenvererbung (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mit einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
