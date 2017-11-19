---
title: "Die Eigenschaft &lt;Eigenschaftsname&gt; kann nicht gelöscht werden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: b3a896e64e048a5104bca84b726c730d4d9d524a
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Die Eigenschaft &lt;Eigenschaftsname&gt; kann nicht gelöscht werden
Die Eigenschaft \<Eigenschaftsname > kann nicht gelöscht werden, da es als festgelegt ist die **Unterscheidungseigenschaft** für die Vererbung zwischen \<Klassenname > und \<Klassenname >  
  
 Die ausgewählte Eigenschaft wird festgelegt, wie die **Unterscheidungseigenschaft** für die Vererbung zwischen den Klassen angegeben, in der Fehlermeldung. Eigenschaften können nicht gelöscht werden, wenn sie zwischen Datenklassen an der Vererbungskonfiguration teilnehmen.  
  
 Legen Sie die **Unterscheidungseigenschaft** auf eine andere Eigenschaft der Datenklasse fest, die die gewünschte Eigenschaft gelöscht werden kann.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Wählen Sie im O/R-Designer die Vererbungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.  
  
2.  Legen Sie die **Unterscheidungseigenschaft** Eigenschaft auf eine andere Eigenschaft.  
  
3.  Versuchen Sie erneut, die Eigenschaft zu löschen.  
  
## <a name="see-also"></a>Siehe auch
[O/R-Designer-Nachrichten](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)