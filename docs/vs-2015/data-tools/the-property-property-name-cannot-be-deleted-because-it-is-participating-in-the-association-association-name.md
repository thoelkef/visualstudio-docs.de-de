---
title: Die Eigenschaft &lt;Eigenschaftennamen&gt; kann nicht gelöscht werden, da sie in der Zuordnung teilnimmt &lt;Zuordnungsname&gt; | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 348dc0cdce8345f0b7de4fb15dcd7175f496dba7
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652917"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Die Eigenschaft &lt;Eigenschaftenname&gt; kann nicht gelöscht werden, da sie Teil der Zuordnung &lt;Zuordnungsname&gt; ist
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die ausgewählte Eigenschaft wurde als **Zuordnungseigenschaft** für die Zuordnung zwischen den in der Fehlermeldung angegebenen Klassen festgelegt. Eigenschaften können nicht gelöscht werden, wenn sie an einer Zuordnung zwischen Datenklassen beteiligt sind.  
  
 Legen Sie die **Zuordnungseigenschaft** auf eine andere Eigenschaft der Datenklasse fest, damit die gewünschte Eigenschaft gelöscht werden kann.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Wählen Sie im O/R-Designer die Zuordnungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.  
  
2.  Doppelklicken Sie auf die Linie, um das Dialogfeld **Zuordnungs-Editor** zu öffnen.  
  
3.  Entfernen Sie die Eigenschaft aus den **Zuordnungseigenschaften**.  
  
4.  Versuchen Sie erneut, die Eigenschaft zu löschen.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Vorgehensweise: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
