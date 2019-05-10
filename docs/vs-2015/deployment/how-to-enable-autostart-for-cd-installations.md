---
title: 'Vorgehensweise: Aktivieren von AutoStart für Installationen von CD | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061098"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Vorgehensweise: Aktivieren von AutoStart für Installationen von CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei der Bereitstellung ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung über Wechselmedien wie z. B. CD-ROM oder DVD-ROM können `AutoStart` , damit die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung wird automatisch gestartet, wenn das Medium eingelegt ist.  
  
 `AutoStart` kann aktiviert werden, auf die **veröffentlichen** auf der Seite die **Projekt-Designer**.  
  
### <a name="to-enable-autostart"></a>Aktivieren von AutoStart  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Klicken Sie auf die Schaltfläche **Optionen**.  
  
     Die **Veröffentlichungsoptionen** Dialogfeld wird angezeigt.  
  
4. Klicken Sie auf **Bereitstellung**.  
  
5. Wählen Sie die **für CD-Installationen automatisch Setup starten, wenn CD eingelegt wird** Kontrollkästchen.  
  
     Eine Autorun.inf-Datei wird an den Veröffentlichungsort kopiert werden, wenn die Anwendung veröffentlicht wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
