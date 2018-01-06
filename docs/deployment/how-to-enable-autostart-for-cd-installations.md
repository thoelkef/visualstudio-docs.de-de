---
title: "Vorgehensweise: Aktivieren von AutoStart für Installationen von CD | Microsoft Docs"
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
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: e830e1be1b7b36e53fd45bc11457452db805ae02
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Gewusst wie: Aktivieren von AutoStart für Installationen von CD
Bei der Bereitstellung einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mithilfe von Wechselmedien wie z. B. CD-ROM oder DVD-ROM-Anwendung, die Sie aktivieren `AutoStart` , damit die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung beim Einlegen des Datenträgers automatisch gestartet wird.  
  
 `AutoStart`kann aktiviert werden, auf die **veröffentlichen** auf der Seite der **Projekt-Designer**.  
  
### <a name="to-enable-autostart"></a>Aktivieren von AutoStart  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Optionen** Schaltfläche.  
  
     Die **Veröffentlichungsoptionen** Dialogfeld wird angezeigt.  
  
4.  Klicken Sie auf **Bereitstellung**.  
  
5.  Wählen Sie die **für CD-Installationen automatisch Setup starten, wenn CD eingelegt wird** Kontrollkästchen.  
  
     Eine Datei "Autorun.inf" wird an den Veröffentlichungsort kopiert werden, wenn die Anwendung veröffentlicht wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)