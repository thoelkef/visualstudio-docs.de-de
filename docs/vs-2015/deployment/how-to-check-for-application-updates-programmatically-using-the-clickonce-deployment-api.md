---
title: 'Vorgehensweise: Suchen nach Anwendungsupdates programmgesteuert mithilfe der API für der ClickOnce-Bereitstellung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ecb3ba8e0fd05e0fb0cd79cde32abe235af743e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509089"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Gewusst wie: Programmgesteuertes Suchen nach Anwendungsupdates mit der API für die ClickOnce-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Überprüfen Sie für die Anwendung programmgesteuert Updates mithilfe der ClickOnce-Bereitstellung-API](https://docs.microsoft.com/visualstudio/deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api).  
  
ClickOnce bietet zwei Möglichkeiten, eine Anwendung zu aktualisieren, nachdem er bereitgestellt wurde. In der ersten Methode können Sie die ClickOnce-Bereitstellung automatisch nach Updates, die in bestimmten Intervallen suchen konfigurieren. In der zweiten Methode schreiben Sie Code, verwendet der <xref:System.Deployment.Application.ApplicationDeployment> Klasse, um nach Updates suchen auf der Grundlage von Ereignissen, wie eine benutzeranforderung.  
  
 Die folgenden Verfahren von Code für ein Programmgesteuertes Update anzeigen und außerdem wird beschrieben, wie Sie zum Konfigurieren der ClickOnce-Bereitstellung zum programmgesteuerten Suche nach Updates zu aktivieren.  
  
 Um eine ClickOnce-Anwendung programmgesteuert aktualisieren, müssen Sie einen Speicherort auf Updates angeben. Dies wird manchmal als Bereitstellungsanbieter bezeichnet. Weitere Informationen zum Festlegen dieser Eigenschaft finden Sie unter [Auswählen einer Strategie der ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Sie können auch das Verfahren unten, um die Anwendung von einem Speicherort bereitstellen, aber von einem anderen aktualisieren. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben eines anderen Speicherorts für Bereitstellungsaktualisierungen](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Programmgesteuert nach Updates suchen  
  
1.  Erstellen Sie eine neue Windows Forms-Anwendung unter Verwendung Ihrer bevorzugten Befehlszeilen- oder visuellen Tools.  
  
2.  Erstellen beliebige Schaltfläche, ein Menüelement oder andere Benutzeroberflächenelemente, die Ihre Benutzer auswählen, um nach Updates suchen sollen. Rufen Sie die folgende Methode zum Suchen und installieren Sie Updates von Ereignishandler des Elements.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3.  Kompilieren Sie Ihre Anwendung.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Verwenden Mage.exe zum Bereitstellen einer Anwendung, die programmgesteuert nach Updates sucht  
  
-   Befolgen Sie die Anweisungen für die Bereitstellung Ihrer Anwendung verwenden Mage.exe, wie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Beim Aufrufen von Mage.exe um das Bereitstellungsmanifest zu generieren, stellen Sie sicher, mit der Befehlszeilenoption `providerUrl`, und die URL an, in dem ClickOnce nach Updates suchen soll. Wenn Ihre Anwendung von update [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), der Aufruf, um das Bereitstellungsmanifest zu generieren könnte beispielsweise wie folgt aussehen:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Verwenden Sie zum Bereitstellen einer Anwendung, die programmgesteuert nach Updates sucht MageUI.exe  
  
-   Befolgen Sie die Anweisungen für die Bereitstellung Ihrer Anwendung verwenden Mage.exe, wie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Auf der **Bereitstellungsoptionen** Registerkarte die **Startposition** Feld in das Anwendungsmanifest ClickOnce nach Updates suchen soll. Auf der **Updateoptionen** Registerkarte die **diese Anwendung soll nach Updates suchen** Kontrollkästchen.  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Ihre Anwendung benötigen Berechtigungen für volle Vertrauenswürdigkeit mit programmgesteuerten Aktualisieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Angeben eines anderen Speicherorts für Bereitstellungsaktualisierungen](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)



