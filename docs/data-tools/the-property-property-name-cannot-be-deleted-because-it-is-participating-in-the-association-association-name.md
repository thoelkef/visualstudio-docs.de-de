---
title: "Die Eigenschaft &lt;Eigenschaftsname&gt; kann nicht gelöscht werden, da sie in der Zuordnung teilnimmt &lt;Zuordnungsname&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 150d176c105e8368fc97f36a19774824dcb91c3e
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Die Eigenschaft &lt;Eigenschaftsname&gt; kann nicht gelöscht werden, da sie in der Zuordnung teilnimmt &lt;Zuordnungsname&gt;
Die ausgewählte Eigenschaft wird festgelegt, wie die **Zuordnungseigenschaft** für die Zuordnung zwischen den Klassen angegeben, in der Fehlermeldung. Eigenschaften können nicht gelöscht werden, wenn sie an einer Zuordnung zwischen Datenklassen beteiligt sind.  
  
 Legen Sie die **Zuordnungseigenschaft** auf eine andere Eigenschaft der Datenklasse fest, die die gewünschte Eigenschaft gelöscht werden kann.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Wählen Sie im O/R-Designer die Zuordnungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.  
  
2.  Doppelklicken Sie auf die Zeile zum Öffnen der **Zuordnungs-Editor** (Dialogfeld).  
  
3.  Entfernen Sie die Eigenschaft aus der **Zuordnungseigenschaften**.  
  
4.  Versuchen Sie erneut, die Eigenschaft zu löschen.  
  
## <a name="see-also"></a>Siehe auch
[O/R-Designer-Nachrichten](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)