---
title: 'Vorgehensweise: Aktivieren von AutoStart für Installationen von CD | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2fde610731ca5ec315b94d2e46f58edb2a7b56fa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273142"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Gewusst wie: Aktivieren von AutoStart für Installationen von CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei der Bereitstellung ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung über Wechselmedien wie z. B. CD-ROM oder DVD-ROM können `AutoStart` , damit die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung wird automatisch gestartet, wenn das Medium eingelegt ist.  
  
 `AutoStart` kann aktiviert werden, auf die **veröffentlichen** auf der Seite die **Projekt-Designer**.  
  
### <a name="to-enable-autostart"></a>Aktivieren von AutoStart  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Optionen** Schaltfläche.  
  
     Die **Veröffentlichungsoptionen** Dialogfeld wird angezeigt.  
  
4.  Klicken Sie auf **Bereitstellung**.  
  
5.  Wählen Sie die **für CD-Installationen automatisch Setup starten, wenn CD eingelegt wird** Kontrollkästchen.  
  
     Eine Autorun.inf-Datei wird an den Veröffentlichungsort kopiert werden, wenn die Anwendung veröffentlicht wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



