---
title: 'Vorgehensweise: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ClickOnce applications
- ClickOnce deployment, debugging
- ClickOnce applications, debugging
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 535ae11811db3117448bf619c0391b852bd65c67
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961183"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Vorgehensweise: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Als Entwickler führen Sie wahrscheinlich Ihre Entwicklungscomputer mit der Berechtigungen „Voll vertrauenswürdig“ aus, daher werden Sie nicht die gleichen Sicherheitsausnahmen beim Debuggen einer ClickOnce-Anwendung sehen, die der Endbenutzer möglicherweise sieht, wenn sie mit eingeschränkten Berechtigungen ausgeführt wird.  
  
 Um diese Ausnahmen zu erfassen, müssen Sie die Anwendung mit genau den Berechtigungen debuggen, die ein Endbenutzer hat. Debuggen mit eingeschränkten Berechtigungen kann im **Projekt-Designer** auf der Seite **Sicherheit**aktiviert werden.  
  
 Wenn Sie darüber hinaus Anwendungen entwickeln, die Webdienste aufrufen, befinden sich diese Webdienste häufig auf Ihrem Entwicklungscomputer. Nach der Bereitstellung greift der Endbenutzer auf diese Webdienste von einer anderen URL aus zu. Zum Emulieren der Endbenutzererfahrung während des Debuggens können Sie eine URL angeben, und der Debugger wird die Webdienste daraufhin so behandeln, als würden Sie von dieser URL aufgerufen werden.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>So aktivieren Sie das Debuggen mit eingeschränkten Berechtigungen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie im **Projekt-Designer**auf die Registerkarte **Sicherheit** .  
  
3.  Wählen Sie das Kontrollkästchen **Enable ClickOnce Security Setting** (ClickOnce-Sicherheitseinstellung aktivieren) aus, und klicken Sie dann auf das Optionsfeld **Teilweise vertrauenswürdige Anwendung** .  
  
4.  Klicken Sie auf die Schaltfläche **Erweitert** .  
  
5.  Wählen Sie das Kontrollkästchen **Diese Anwendung mit dem ausgewählten Berechtigungssatz &amp;debuggen** aus, und klicken Sie dann auf **OK**.  
  
     Wenn Sie die Anwendung debuggen, lösen alle Zugriffsversuche auf eine Berechtigung, die nicht Teil des Berechtigungssatzes ist, eine Sicherheitsausnahme aus.  
  
### <a name="to-specify-a-url-for-debugging"></a>So geben Sie eine URL für das Debuggen an  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie im **Projekt-Designer**auf die Registerkarte **Sicherheit** .  
  
3.  Wählen Sie das Kontrollkästchen **Enable ClickOnce Security Setting** (ClickOnce-Sicherheitseinstellung aktivieren) aus, und klicken Sie dann auf das Optionsfeld **Teilweise vertrauenswürdige Anwendung** .  
  
4.  Klicken Sie auf die Schaltfläche **Erweitert** .  
  
5.  Wählen Sie das Kontrollkästchen **Diese Anwendung mit dem ausgewählten Berechtigungssatz &amp;debuggen** aus, und klicken Sie dann auf **OK**.  
  
6.  Geben Sie im Textfeld **Diese Anwendung debuggen, als ob sie von folgender URL heruntergeladen würde:** eine URL oder einen Netzwerkpfad ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Festlegen Sie benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
