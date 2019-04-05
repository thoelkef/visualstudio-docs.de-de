---
title: 'Vorgehensweise: Suchen nach Anwendungsupdates programmgesteuert mithilfe der API für der ClickOnce-Bereitstellung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: ac7a5665b287f51e59d99d21802acc252a55a99a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960770"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Vorgehensweise: Suchen Sie nach Anwendungsupdates programmgesteuert mithilfe der API für der ClickOnce-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
-   Befolgen Sie die Anweisungen für die Bereitstellung Ihrer Anwendung verwenden Mage.exe, wie unter [Exemplarische Vorgehensweise: Manually Deploying a ClickOnce Application (Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung)](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Beim Aufrufen von Mage.exe um das Bereitstellungsmanifest zu generieren, stellen Sie sicher, mit der Befehlszeilenoption `providerUrl`, und die URL an, in dem ClickOnce nach Updates suchen soll. Wenn Ihre Anwendung von update [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), der Aufruf, um das Bereitstellungsmanifest zu generieren könnte beispielsweise wie folgt aussehen:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Verwenden Sie zum Bereitstellen einer Anwendung, die programmgesteuert nach Updates sucht MageUI.exe  
  
-   Befolgen Sie die Anweisungen für die Bereitstellung Ihrer Anwendung verwenden Mage.exe, wie unter [Exemplarische Vorgehensweise: Manually Deploying a ClickOnce Application (Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung)](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Auf der **Bereitstellungsoptionen** Registerkarte die **Startposition** Feld in das Anwendungsmanifest ClickOnce nach Updates suchen soll. Auf der **Updateoptionen** Registerkarte die **diese Anwendung soll nach Updates suchen** Kontrollkästchen.  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Ihre Anwendung benötigen Berechtigungen für volle Vertrauenswürdigkeit mit programmgesteuerten Aktualisieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Angeben eines anderen Speicherorts für Bereitstellungsaktualisierungen](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
