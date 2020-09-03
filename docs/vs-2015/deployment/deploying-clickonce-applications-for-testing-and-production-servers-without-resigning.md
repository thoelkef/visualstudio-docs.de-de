---
title: Bereitstellen von ClickOnce-Anwendungen für Test-und Produktionsserver ohne erneutes Signieren | Microsoft-Dokumentation
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
ms.openlocfilehash: a8e41e67d5e2800acc41e1220fe632001420a274
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395371"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne erneutes Signieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird eine neue Funktion von ClickOnce erläutert, die in der .NET Framework Version 3,5 eingeführt wurde, die die Bereitstellung von ClickOnce-Anwendungen von mehreren Netzwerk Standorten aus ermöglicht, ohne dass die ClickOnce-Manifeste neu signiert oder geändert werden  
  
> [!NOTE]
> Das erneute Signieren ist nach wie vor die bevorzugte Methode für die Bereitstellung neuer Versionen von Anwendungen. Verwenden Sie nach Möglichkeit die Methode zum erneuten Signieren. Weitere Informationen finden Sie unter [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Entwickler und ISVs von Drittanbietern können diese Funktion abonnieren, was ihren Kunden die Aktualisierung Ihrer Anwendungen erleichtert. Diese Funktion kann in den folgenden Situationen verwendet werden:  
  
- Beim Aktualisieren einer Anwendung, nicht bei der ersten Installation einer Anwendung.  
  
- Wenn es nur eine Konfiguration der Anwendung auf einem Computer gibt. Wenn beispielsweise eine Anwendung so konfiguriert ist, dass Sie auf zwei unterschiedliche Datenbanken verweist, können Sie diese Funktion nicht verwenden.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>"DeploymentProvider" von Bereitstellungs Manifesten ausschließen  
 In den .NET Framework 2,0 und .NET Framework 3,0 muss jede ClickOnce-Anwendung, die auf dem System zur Offline Verfügbarkeit installiert wird, `deploymentProvider` im Bereitstellungs Manifest einen angeben. Wird `deploymentProvider` häufig als Update Speicherort bezeichnet. Hierbei handelt es sich um den Speicherort, an dem ClickOnce auf Anwendungs Updates überprüft wird. Diese Anforderung ist in Verbindung mit der Anforderung, dass Anwendungs Herausgeber ihre bereit Stellungen signieren müssen, für ein Unternehmen schwierig, eine ClickOnce-Anwendung von einem Hersteller oder anderen Drittanbietern zu aktualisieren. Außerdem ist es schwieriger, dieselbe Anwendung von mehreren Speicherorten im gleichen Netzwerk aus bereitzustellen.  
  
 Mit den Änderungen, die im .NET Framework 3,5 an ClickOnce vorgenommen wurden, ist es möglich, dass ein Drittanbieter eine ClickOnce-Anwendung für eine andere Organisation bereitstellt, die dann die Anwendung in einem eigenen Netzwerk bereitstellen kann.  
  
 Um dieses Feature nutzen zu können, müssen Entwickler von ClickOnce-Anwendungen `deploymentProvider` von ihren Bereitstellungs Manifesten ausschließen. Dies bedeutet `-providerUrl` , dass das Argument beim Erstellen von Bereitstellungs Manifesten mit Mage.exe ausgeschlossen wird oder dass das Textfeld **Startort** auf der Registerkarte Anwendungs Manifest leer bleibt, wenn Sie Bereitstellungs **Manifeste** mit MageUI.exe erzeugen.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider und Anwendungs Updates  
 Ab dem .NET Framework 3,5 müssen Sie `deploymentProvider` in Ihrem Bereitstellungs Manifest keinen mehr angeben, um eine ClickOnce-Anwendung für die Online-und Offline Verwendung bereitzustellen. Dies unterstützt das Szenario, in dem Sie die Bereitstellung selbst verpacken und signieren müssen, andere Unternehmen jedoch die Bereitstellung der Anwendung über ihre Netzwerke erlauben.  
  
 Der wichtigste Punkt ist, dass Anwendungen, die eine ausschließen `deploymentProvider` , den Installationsort während der Updates nicht ändern können, bis Sie ein Update mit dem `deploymentProvider` Tag erneut senden.  
  
 Es folgen zwei Beispiele, um diesen Punkt zu verdeutlichen. Im ersten Beispiel veröffentlichen Sie eine ClickOnce-Anwendung, die kein `deploymentProvider` Tag hat, und Sie bitten Benutzer, Sie aus zu installieren `http://www.adatum.com/MyApplication/` . Wenn Sie das nächste Update der Anwendung aus veröffentlichen möchten `http://subdomain.adatum.com/MyApplication/` , haben Sie keine Möglichkeit, dies im Bereitstellungs Manifest zu signalisieren, das sich in befindet `http://www.adatum.com/MyApplication/` . Sie haben zwei Möglichkeiten:  
  
- Teilen Sie den Benutzern mit, dass Sie die vorherige Version deinstallieren, und installieren Sie die neue Version am neuen Speicherort.  
  
- Fügen Sie ein Update für `http://www.adatum.com/MyApplication/` ein, das eine enthält `deploymentProvider` , auf die verweist `http://www.adatum.com/MyApplication/` . Anschließend können Sie später ein weiteres Update freigeben, das `deploymentProvider` auf verweist `http://subdomain.adatum.com/MyApplication/` .  
  
  Im zweiten Beispiel veröffentlichen Sie eine ClickOnce-Anwendung, die angibt `deploymentProvider` und Sie dann entfernen. Sobald die neue Version ohne `deploymentProvider` auf Clients heruntergeladen wurde, können Sie den für Updates verwendeten Pfad erst umleiten, wenn Sie eine Version der `deploymentProvider` wiederhergestellten Anwendung freigeben. Wie im ersten Beispiel, `deploymentProvider` muss zunächst auf den aktuellen Update Speicherort und nicht auf den neuen Speicherort zeigen. Wenn Sie in diesem Fall versuchen, eine einzufügen, `deploymentProvider` die auf verweist `http://subdomain.adatum.com/MyApplication/` , schlägt das nächste Update fehl.  
  
## <a name="creating-a-deployment"></a>Erstellen einer Bereitstellung  
 Eine Schritt-für-Schritt-Anleitung zum Erstellen von bereit Stellungen, die von verschiedenen Netzwerk Standorten aus bereitgestellt werden können, finden Sie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung, für die keine erneute Signierung erforderlich](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)ist  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
