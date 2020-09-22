---
title: 'Gewusst wie: Aktivieren von ClickOnce-Sicherheitseinstellungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1b104a7a0451da7f772077d2f566b36b9f601c17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840973"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Gewusst wie: Aktivieren von ClickOnce-Sicherheitseinstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Code Zugriffssicherheit für ClickOnce-Anwendungen muss aktiviert sein, um die Anwendung zu veröffentlichen. Dies erfolgt automatisch, wenn Sie eine Anwendung mit dem Webpublishing-Assistenten veröffentlichen.  
  
 In einigen Fällen kann das Aktivieren der Code Zugriffssicherheit beim entwickeln oder Debuggen der Anwendung die Leistung beeinträchtigen. in diesen Fällen möchten Sie möglicherweise die Sicherheitseinstellungen vorübergehend deaktivieren.  
  
 Die ClickOnce-Sicherheitseinstellungen können auf der Seite **Sicherheit** des **Projekt-Designers**aktiviert oder deaktiviert werden.  
  
### <a name="to-enable-clickonce-security-settings"></a>So aktivieren Sie die ClickOnce-Sicherheitseinstellungen  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Sicherheit** .  
  
3. Aktivieren Sie das Kontrollkästchen **ClickOnce-Sicherheitseinstellungen aktivieren** .  
  
     Nun können Sie die Sicherheitseinstellungen für Ihre Anwendung auf der Seite Sicherheit anpassen.  
  
    > [!NOTE]
    > Dieses Kontrollkästchen wird automatisch ausgewählt, wenn die Anwendung mit dem **Veröffentlichungs** -Assistenten veröffentlicht wird.  
  
### <a name="to-disable-clickonce-security-settings"></a>So deaktivieren Sie die ClickOnce-Sicherheitseinstellungen  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Sicherheit** .  
  
3. Deaktivieren Sie das Kontrollkästchen **ClickOnce-Sicherheitseinstellungen aktivieren** .  
  
     Ihre Anwendung wird mit den Sicherheitseinstellungen für die volle Vertrauenswürdigkeit ausgeführt. Alle Einstellungen auf der Seite **Sicherheit** werden ignoriert.  
  
    > [!NOTE]
    > Jedes Mal, wenn die Anwendung mit dem Veröffentlichungs-Assistenten veröffentlicht wird, wird dieses Kontrollkästchen aktiviert. Sie müssen Sie nach jeder erfolgreichen Veröffentlichung erneut löschen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Code Zugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
