---
title: 'Vorgehensweise: Angeben der offline- oder ClickOnce Onlineinstallationsmodus | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1515d9b9b12d92f7189c1dda59659d6ea1c03d5
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080172"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Gewusst wie: angeben die ClickOnce offline oder online-Installationsmodus
Die `Install Mode` für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung bestimmt, ob die Anwendung offline oder online verfügbar sein wird. Bei der Auswahl **die Anwendung ist nur online verfügbar**, die Benutzer benötigen Zugriff auf die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Veröffentlichungsort (einer Webseite oder eine Dateifreigabe) um die Anwendung auszuführen. Bei der Auswahl **der Anwendung ist auch offline verfügbar**, Einträge für die Anwendung hinzugefügt der **starten** Menü und die **Software** Dialogfeld; der Benutzer ist um die Anwendung auszuführen, wenn sie nicht verbunden werden können.  
  
 Die `Install Mode` kann festgelegt werden, auf die **veröffentlichen** auf der Seite die **Projekt-Designer**.  
  
 **Beachten Sie** der `Install Mode` kann auch mithilfe des Veröffentlichungs-Assistenten festgelegt werden. Weitere Informationen finden Sie unter [Vorgehensweise: veröffentlichen eine ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Um eine ClickOnce-Anwendung nur online verfügbar machen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  In der **Installationsmodus und-Einstellungen** Bereich, klicken Sie auf die **die Anwendung ist nur online verfügbar** Optionsfeld aus.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Um eine ClickOnce-Anwendung online oder offline verfügbar machen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  In der **Installationsmodus und-Einstellungen** Bereich, klicken Sie auf die **der Anwendung ist auch offline verfügbar** Optionsfeld aus.  
  
     Bei der Installation die Anwendung Einträge hinzugefügt der **starten** Menü und **Software** in der Systemsteuerung.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: veröffentlichen eine ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Wählen Sie eine Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)