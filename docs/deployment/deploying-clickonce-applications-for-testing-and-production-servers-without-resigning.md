---
title: "Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne erneutes Signieren | Microsoft Docs"
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
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: ec7265f91d5c202d5885b7f1994aa6f037d6d2ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne erneutes Signieren
In diesem Thema wird erläutert, ein neues Feature von ClickOnce in .NET Framework Version 3.5, die die Bereitstellung von ClickOnce-Anwendungen über mehrere Netzwerkadressen ermöglicht, ohne erneutes Signieren, oder ändern die ClickOnce-Manifeste eingeführt wird.  
  
> [!NOTE]
>  Erneutes Signieren ist immer noch die bevorzugte Methode für die Bereitstellung neuer Versionen von Anwendungen. Verwenden Sie nach Möglichkeit diese Methode. Weitere Informationen finden Sie unter [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Entwickler von Drittanbietern und ISVs können auf dieses Feature teilnehmen für ihre Kunden zum Aktualisieren von ihren Anwendungen einfacher zu machen. Diese Funktion kann in den folgenden Situationen verwendet:  
  
-   Wenn eine Anwendung, nicht der ersten Installation einer Anwendung zu aktualisieren.  
  
-   Wenn nur eine Konfiguration der Anwendung auf einem Computer vorhanden ist. Z. B. wenn eine Anwendung konfiguriert ist, um auf zwei verschiedene Datenbanken verweisen, kann nicht diese Funktion verwenden.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Ausschließen von "deploymentProvider" von Bereitstellungsmanifeste  
 In .NET Framework 2.0 und .NET Framework 3.0, jede ClickOnce-Anwendung, die für die offlineverfügbarkeit auf dem System installiert angeben muss eine `deploymentProvider` in das Bereitstellungsmanifest. Die `deploymentProvider` wird häufig als Speicherort für die Aktualisierung; bezeichnet es ist der Speicherort, in dem ClickOnce Anwendungsupdates überprüft. Diese Anforderung, gekoppelt mit die Notwendigkeit einer Anwendung Verleger zum Signieren ihrer Bereitstellungen nur schwer für ein Unternehmen eine ClickOnce-Anwendung von einem Hersteller oder andere Drittanbieter-aktualisieren. Es macht es auch schwieriger zu derselben Anwendung von mehreren Speicherorten in einem Netzwerk bereitstellen.  
  
 Mit ClickOnce in .NET Framework 3.5 vorgenommenen Änderungen, ist es möglich, dass ein Drittanbieter-eine ClickOnce-Anwendung auf einer anderen Organisation bereitgestellt, die dann die Anwendung in einem eigenen Netzwerk bereitstellen können.  
  
 Um dieses Feature nutzen zu können, müssen Entwickler von ClickOnce-Anwendungen ausschließen `deploymentProvider` Manifeste aus ihrer Bereitstellung. Dies bedeutet, dass mit Ausnahme der `-providerUrl` Argument beim Erstellen der Bereitstellung Manifeste mit Mage.exe oder sicherstellen, die **Speicherort starten** Textfeld auf der **Anwendungsmanifest** Registerkarte gelassen Wenn Sie Bereitstellungsmanifeste mit MageUI.exe generieren.  
  
## <a name="deploymentprovider-and-application-updates"></a>"deploymentProvider" und Anwendungsupdates  
 Ab .NET Framework 3.5, nicht mehr haben Sie an einer `deploymentProvider` das Bereitstellungsmanifest zum Bereitstellen einer ClickOnce-Anwendung für die Verwendung von Online- und Offlineanalyse. Dies unterstützt das Szenario, in denen Sie müssen zum Packen und Signieren der Bereitstellung selbst, aber ermöglichen anderen Unternehmen, um die Anwendung über ihre Netzwerke bereitzustellen.  
  
 Wichtig zu beachten ist, die Anwendungen, die Ausschließen einer `deploymentProvider` ihre Installationsspeicherort kann nicht während eines Updates, geändert werden, bis sie ein Update ausgeliefert, die enthält die `deploymentProvider` tag erneut aus.  
  
 Hier sind zwei Beispiele zu diesem Zeitpunkt zu verdeutlichen. Im ersten Beispiel, die Sie Veröffentlichen einer ClickOnce-Anwendung, die keine `deploymentProvider` Tag, und Sie bitten Sie Benutzer zur Installation von http://www.adatum.com/MyApplication/. Wenn Sie sich, dass Sie das nächste Update der Anwendung von http://subdomain.adatum.com/MyApplication/ aus veröffentlichen möchten entscheiden, müssen Sie keine Möglichkeit, dies im Bereitstellungsmanifest, das http://www.adatum.com/MyApplication/ befindet. Sie können eine der zwei Aufgaben ausführen:  
  
-   Bitten Sie Benutzer, die frühere Version deinstallieren und installieren Sie die neue Version von den neuen Speicherort.  
  
-   Ein Update auf, die enthält http://www.adatum.com/MyApplication/ umfassen eine `deploymentProvider` auf http://www.adatum.com/MyApplication/ verweist. Klicken Sie dann ein anderes Update später mit Version `deploymentProvider` auf http://subdomain.adatum.com/MyApplication/ verweist.  
  
 Im zweiten Beispiel veröffentlichen Sie eine ClickOnce-Anwendung, der angibt, `deploymentProvider`, und Sie dann entscheiden, um ihn zu entfernen. Nachdem die neue Version ohne `deploymentProvider` heruntergeladen wurde an Clients nicht werden umleiten den Pfad für Updates verwendet, bis Sie eine Version der Anwendung freigeben, die hat `deploymentProvider` wiederhergestellt. Wie bei im ersten Beispiel `deploymentProvider` muss zunächst auf den aktuellen Speicherort für Update, nicht auf den neuen Pfad verweisen. In diesem Fall, wenn Sie versuchen, fügen Sie eine `deploymentProvider` , die auf http://subdomain.adatum.com/MyApplication/ verweist, und klicken Sie dann das nächste Update schlägt fehl.  
  
## <a name="creating-a-deployment"></a>Erstellen einer Bereitstellung  
 Schritt-für-Schritt-Anleitungen zum Erstellen von Bereitstellungen, die von verschiedenen Netzwerkorten bereitgestellt werden können, finden Sie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung, ist nicht erforderlich Re-Signing und behält Branding-Informationen](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>Siehe auch  
 [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [„MageUI.exe“ (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)