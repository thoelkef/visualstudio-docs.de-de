---
title: "Vorgehensweise: Ändern der Veröffentlichungssprache einer ClickOnce-Anwendung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: "19"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1643a3bec79b6f0e1b89548ab1a62c3dfd6c6e9a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Gewusst wie: Ändern der Veröffentlichungssprache einer ClickOnce-Anwendung
Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, die Benutzeroberfläche während der Installation standardmäßig die Sprache und Kultur des Entwicklungscomputers angezeigt. Bei Veröffentlichung bei eine lokalisierte Anwendung, müssen Sie eine Sprache und Kultur, mit der lokalisierte Version übereinstimmen angeben. Dies richtet sich nach der `Publish language` -Eigenschaft für das Projekt.  
  
 Die `Publish language` Eigenschaft kann festgelegt werden, der **Veröffentlichungsoptionen** (Dialogfeld), über die **veröffentlichen** auf der Seite der **Projekt-Designer**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-change-the-publish-language"></a>So ändern Sie die Sprache für Veröffentlichung  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Optionen** die Schaltfläche, um die **Veröffentlichungsoptionen** (Dialogfeld).  
  
4.  Klicken Sie auf **Beschreibung**.  
  
5.  In der **Veröffentlichungsoptionen** Dialogfeld Feld, wählen Sie eine Sprache und Kultur aus der **Sprache für Veröffentlichung** Dropdown-Liste, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)