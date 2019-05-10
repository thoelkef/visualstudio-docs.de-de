---
title: Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne erneutes Signieren | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c7cc8a9d1767a289112b18dbfe7c81b9a010bae
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422784"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne erneutes Signieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein neues Feature von ClickOnce eingeführt, die in .NET Framework Version 3.5, die die Bereitstellung von ClickOnce-Anwendungen über mehrere Speicherorte zu, ohne erneutes Signieren oder Ändern der ClickOnce können-Manifeste in diesem Thema.  
  
> [!NOTE]
> Erneutes Signieren ist immer noch die bevorzugte Methode zum Bereitstellen neuer Versionen von Anwendungen. Verwenden Sie diese Methode, nach Möglichkeit. Weitere Informationen finden Sie unter [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Drittanbieter-Entwicklern und ISVs können zu diesem Feature teilnehmen erleichtert Ihnen die für ihre Kunden ihre Anwendungen zu aktualisieren. Diese Funktion kann in den folgenden Situationen verwendet werden:  
  
- Beim Aktualisieren von einer Anwendung, die nicht in der ersten Installation einer Anwendung.  
  
- Wenn nur eine Konfiguration der Anwendung auf einem Computer vorhanden ist. Wenn eine Anwendung konfiguriert ist, um auf zwei verschiedenen Datenbanken verweisen, können nicht Sie z. B. diese Funktion verwenden.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Ausschließen von "deploymentProvider" von Bereitstellungsmanifesten  
 In .NET Framework 2.0 und .NET Framework 3.0, jede ClickOnce-Anwendung, die für die offlineverfügbarkeit auf dem System installiert angeben muss eine `deploymentProvider` in das Bereitstellungsmanifest. Die `deploymentProvider` wird bezeichnet als Speicherort für die Aktualisierung; es ist der Speicherort, in dem ClickOnce Anwendungsupdates überprüft. Diese Anforderung, die Notwendigkeit von App-Herausgeber ihre Bereitstellungen anmelden gekoppelt war es schwierig für ein Unternehmen eine ClickOnce-Anwendung von einem Lieferanten oder anderen von Drittanbietern zu aktualisieren. Es erleichtert auch schwieriger zu derselben Anwendung von mehreren Standorten in einem Netzwerk bereitstellen.  
  
 Mit Änderungen, die von ClickOnce in .NET Framework 3.5 vorgenommen wurden, ist es möglich, dass ein Drittanbieter-zu einer ClickOnce-Anwendung an eine andere Organisation, die dann die Anwendung auf einem eigenen Netzwerk bereitstellen können.  
  
 Um dieses Feature nutzen zu können, müssen Entwickler von ClickOnce-Anwendungen ausschließen `deploymentProvider` Manifeste aus ihrer Bereitstellung. Dies bedeutet, dass mit Ausnahme der `-providerUrl` Argument bei der Erstellung der Bereitstellung von zielmanifesten mit Mage.exe, und stellen Sie sicher, dass die **Speicherort starten** Textfeld auf die **Anwendungsmanifest** Registerkarte ist leer, wenn Sie Bereitstellungsmanifeste mit MageUI.exe generieren.  
  
## <a name="deploymentprovider-and-application-updates"></a>"deploymentProvider" und Anwendungsupdates  
 Ab .NET Framework 3.5 können Sie nicht mehr an haben eine `deploymentProvider` das Bereitstellungsmanifest zum Bereitstellen einer ClickOnce-Anwendung für die Nutzung von Online- und Offlineanalyse. Dadurch wird das Szenario, in denen man, Packen und Signieren der Bereitstellung selbst können jedoch andere Unternehmen mit der Bereitstellung der Anwendung über ihre Netzwerke, unterstützt.  
  
 Der wichtigste Punkt hierbei ist, Anwendungen, die ausgeschlossen eine `deploymentProvider` ihren Installationspfad kann nicht während eines Updates, geändert werden, bis sie ein Update ausgeliefert, die enthält die `deploymentProvider` tag erneut aus.  
  
 Hier sind zwei Beispiele, um diesen Punkt zu verdeutlichen. Im ersten Beispiel, die Sie Veröffentlichen einer ClickOnce-Anwendung, die keine `deploymentProvider` -Tag und bitten Sie Benutzer zur Installation von http://www.adatum.com/MyApplication/. Wenn Sie möchten, müssen Sie das nächste Update der Anwendung aus veröffentlichen möchten http://subdomain.adatum.com/MyApplication/, Sie haben keine Möglichkeit, dies im Bereitstellungsmanifest, das befindet http://www.adatum.com/MyApplication/. Sie können eine der beiden Aktionen ausführen:  
  
- Weisen Sie Ihre Benutzer auf die vorherige Version deinstallieren und installieren Sie die neue Version vom neuen Speicherort.  
  
- Sind Sie ein Update auf http://www.adatum.com/MyApplication/ , umfasst eine `deploymentProvider` auf http://www.adatum.com/MyApplication/. Klicken Sie dann Version ein anderes Update später mit `deploymentProvider` auf http://subdomain.adatum.com/MyApplication/.  
  
  Im zweiten Beispiel, die Sie Veröffentlichen einer ClickOnce-Anwendung, der angibt, `deploymentProvider`, und Sie dann entscheiden, um ihn zu entfernen. Nachdem die neue Version ohne `deploymentProvider` heruntergeladen wurde für Clients nicht werden den Pfad für Updates verwendet wird, bis Sie eine Version Ihrer Anwendung freigeben, die umleiten `deploymentProvider` wiederhergestellt. Wie bei der ersten Beispiel `deploymentProvider` muss zunächst in den aktuellen Speicherort der Update, nicht auf den neuen Pfad verweisen. In diesem Fall, wenn Sie versuchen, fügen Sie eine `deploymentProvider` , die auf http://subdomain.adatum.com/MyApplication/, das nächste Update nicht ausgeführt werden.  
  
## <a name="creating-a-deployment"></a>Erstellen einer Bereitstellung  
 Schritt-für-Schritt-Anleitungen zum Erstellen von Bereitstellungen, die von verschiedenen Netzwerkorten bereitgestellt werden können, finden Sie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung, die kein erneutes Signieren erfordert und Brandinginformationen beibehält](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Siehe auch  
 [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [„MageUI.exe“ (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
