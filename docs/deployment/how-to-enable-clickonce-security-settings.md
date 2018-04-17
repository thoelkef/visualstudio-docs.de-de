---
title: 'Vorgehensweise: Aktivieren von ClickOnce-Sicherheitseinstellungen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 5c59786a49f09efd2dc4d906511ac2602c765c07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-enable-clickonce-security-settings"></a>Gewusst wie: Aktivieren von ClickOnce-Sicherheitseinstellungen
Codezugriffssicherheit für ClickOnce-Anwendungen muss aktiviert sein, um die Anwendung zu veröffentlichen. Dies erfolgt automatisch, wenn Sie eine Anwendung mithilfe des Veröffentlichungs-Assistenten veröffentlichen.  
  
 In einigen Fällen kann ein Codezugriffssicherheit aktivieren die Leistung bei der Erstellung oder Debuggen der Anwendung auswirken; in diesen Fällen möchten Sie möglicherweise die Sicherheitseinstellungen vorübergehend deaktivieren.  
  
 ClickOnce-Sicherheitseinstellungen können aktiviert oder deaktiviert die **Sicherheit** auf der Seite der **Projekt-Designer**.  
  
### <a name="to-enable-clickonce-security-settings"></a>ClickOnce-Sicherheitseinstellungen aktivieren  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Sicherheit** .  
  
3.  Aktivieren Sie das Kontrollkästchen **ClickOnce-Sicherheitseinstellungen aktivieren** .  
  
     Sie können jetzt die Sicherheitseinstellungen für Ihre Anwendung auf der Seite "Sicherheit" anpassen.  
  
    > [!NOTE]
    >  Dieses Kontrollkästchen wird automatisch jedes Mal die Anwendung veröffentlicht wird, mit der **veröffentlichen** Assistenten.  
  
### <a name="to-disable-clickonce-security-settings"></a>So deaktivieren Sie die ClickOnce-Sicherheitseinstellungen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Sicherheit** .  
  
3.  Deaktivieren der **ClickOnce-Sicherheitseinstellungen aktivieren** Kontrollkästchen.  
  
     Die Anwendung wird mit den Sicherheitseinstellungen für volle Vertrauenswürdigkeit ausgeführt werden. Alle Einstellungen auf der **Sicherheit** Seite ignoriert werden.  
  
    > [!NOTE]
    >  Jedes Mal, wenn die Anwendung mit dem Webpublishing-Assistenten veröffentlicht wurde, wird dieses Kontrollkästchen aktiviert werden; Sie müssen es nach jeder erfolgreichen Veröffentlichung wieder deaktivieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 
