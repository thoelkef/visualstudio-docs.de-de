---
title: "Vorgehensweise: Überprüfen von Anwendungsupdates programmgesteuert mithilfe der API für der ClickOnce-Bereitstellung | Microsoft Docs"
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
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 02e6a4c0b69bf9e9d6170175b4324ccb226854e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Gewusst wie: Programmgesteuertes Suchen nach Anwendungsupdates mit der API für die ClickOnce-Bereitstellung
ClickOnce bietet zwei Möglichkeiten, eine Anwendung zu aktualisieren, nachdem er bereitgestellt wird. Bei der ersten Methode können Sie die ClickOnce-Bereitstellung automatisch zur Überprüfung auf Updates in bestimmten Intervallen konfigurieren. In der zweiten Methode schreiben Sie Code, der verwendet die <xref:System.Deployment.Application.ApplicationDeployment> klassenbasierter nach Updates suchen, auf ein Ereignis, z. B. eine Anforderung des Benutzers.  
  
 Die folgenden Verfahren zeigen Code für ein Programmgesteuertes Update und auch beschrieben, wie die ClickOnce-Bereitstellung programmgesteuerte updateprüfungen aktivieren konfigurieren.  
  
 Um eine ClickOnce-Anwendung programmgesteuert zu aktualisieren, müssen Sie einen Speicherort für Updates angeben. Dies wird manchmal als Bereitstellungsanbieter bezeichnet. Weitere Informationen zum Festlegen dieser Eigenschaft finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Sie können auch das Bereitstellen der Anwendung von einem Speicherort, aber von einem anderen aktualisieren nachfolgend beschriebene Verfahren verwenden. Weitere Informationen finden Sie unter [wie: Angeben eines anderen Speicherorts für Bereitstellungsaktualisierungen](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Programmgesteuert nach Updates suchen  
  
1.  Erstellen Sie eine neue Windows Forms-Anwendung mit Ihren bevorzugten Befehlszeilen- oder visuellen Tools.  
  
2.  Erstellen beliebige Schaltfläche, ein Menüelement oder andere Benutzer-Element-Schnittstelle, die Benutzer auswählen, nach Updates suchen sollen. Dieses Element-Ereignishandler rufen Sie die folgende Methode zum Überprüfen und Installieren von Updates.  
  
     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  Kompilieren Sie Ihre Anwendung.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Verwenden Mage.exe zum Bereitstellen einer Anwendung, die programmgesteuert nach Updates sucht  
  
-   Befolgen Sie die Anweisungen für die Bereitstellung Ihrer Anwendung verwenden Mage.exe, wie in beschrieben [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Stellen Sie beim Mage.exe, um das Bereitstellungsmanifest zu generieren aufrufen, verwenden Sie die Befehlszeilenoption `providerUrl`, und die URL an, in dem ClickOnce nach Updates suchen soll. Wenn ein die Anwendung von Update [http://www.adatum.com/MyApp](http://www.adatum.com/MyApp), Aufruf Bereitstellungsmanifests generieren könnte beispielsweise folgendermaßen aussehen:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Verwenden Sie zum Bereitstellen einer Anwendung, die Prüfung auf Updates programmgesteuert MageUI.exe  
  
-   Befolgen Sie die Anweisungen für die Bereitstellung Ihrer Anwendung verwenden Mage.exe, wie in beschrieben [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Auf der **Bereitstellungsoptionen** Registerkarte, legen Sie die **Startspeicherort** Feld auf das Anwendungsmanifest ClickOnce nach Updates suchen soll. Auf der **Aktualisierungsoptionen** Registerkarte Deaktivieren der **diese Anwendung soll nach Updates suchen** Kontrollkästchen.  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Ihre Anwendung benötigen Berechtigungen für volle Vertrauenswürdigkeit zum programmgesteuerten Aktualisieren verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Angeben eines alternatives Speicherorts für Bereitstellungsaktualisierungen](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)