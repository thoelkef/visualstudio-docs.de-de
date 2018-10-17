---
title: Die Eigenschaft &lt;Eigenschaftennamen&gt; kann nicht gelöscht werden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98b065500c9c881a7190b59c4d70a0433eb8864c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186523"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Die Eigenschaft &lt;Eigenschaftennamen&gt; kann nicht gelöscht werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Die Eigenschaft \<Eigenschaftenname > kann nicht gelöscht werden, da sie als Unterscheidungseigenschaft für die Vererbung zwischen festgelegt ist \<Klassenname > und \<Klassenname >  
  
 Die ausgewählte Eigenschaft wird festgelegt, als die **Unterscheidungseigenschaft** für die Vererbung zwischen den Klassen, die in der Fehlermeldung angegeben. Eigenschaften können nicht gelöscht werden, wenn sie zwischen Datenklassen an der Vererbungskonfiguration teilnehmen.  
  
 Legen Sie die **Unterscheidungseigenschaft** auf eine andere Eigenschaft der Datenklasse fest, damit die gewünschte Eigenschaft gelöscht werden kann.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Wählen Sie im O/R-Designer die Vererbungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.  
  
2.  Legen Sie die **Diskriminator** Eigenschaft auf eine andere Eigenschaft.  
  
3.  Versuchen Sie erneut, die Eigenschaft zu löschen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Datenklassenvererbung (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mit einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)

