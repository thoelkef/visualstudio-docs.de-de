---
title: 'Vorgehensweise: angeben die ClickOnce Offline oder Onlineinstallationsmodus | Microsoft Docs'
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
ms.openlocfilehash: 18e758def9a92bc4402812dc0e2d665d8acae848
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Gewusst wie: Angeben des Offline- oder Onlineinstallationsmodus von ClickOnce
Die `Install Mode` für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung bestimmt, ob die Anwendung offline oder online zur Verfügung stehen. Bei Auswahl **die Anwendung ist nur online verfügbar**, die Benutzer benötigen Zugriff auf die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Veröffentlichungsort (entweder eine Webseite oder Dateifreigabe) um die Anwendung auszuführen. Bei Auswahl **Anwendung ist ebenfalls offline verfügbar**, die Anwendung Einträge hinzugefügt der **starten** Menü und die **Software** Dialogfeld; der Benutzer ist um die Anwendung auszuführen, wenn keine Verbindung hergestellt werden kann.  
  
 Die `Install Mode` kann festgelegt werden, auf die **veröffentlichen** auf der Seite der **Projekt-Designer**.  
  
 **Hinweis** der `Install Mode` kann auch mithilfe des Veröffentlichungs-Assistenten festgelegt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Um eine ClickOnce-Anwendung nur online verfügbar machen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  In der **Modus installieren und Einstellungen** Bereich, klicken Sie auf die **die Anwendung ist nur online verfügbar** Optionsfeld.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Um eine ClickOnce-Anwendung online oder offline verfügbar machen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  In der **Modus installieren und Einstellungen** Bereich, klicken Sie auf die **die Anwendung ist ebenfalls offline verfügbar** Optionsfeld.  
  
     Während der Installation fügt die Anwendung Einträge in der **starten** Menü und **Software** in der Systemsteuerung.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)