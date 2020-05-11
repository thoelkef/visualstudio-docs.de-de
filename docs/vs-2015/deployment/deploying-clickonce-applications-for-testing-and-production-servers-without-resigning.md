---
title: Bereitstellen von ClickOnce-Anwendungen für Test- und Produktionsserver ohne Neuzuweisung | Microsoft Docs
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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395371"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne erneutes Signieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird eine neue Funktion von ClickOnce erläutert, die in der .NET Framework-Version 3.5 eingeführt wurde und die Bereitstellung von ClickOnce-Anwendungen von mehreren Netzwerkstandorten aus ermöglicht, ohne die ClickOnce-Manifeste neu signieren oder ändern zu müssen.  
  
> [!NOTE]
> Das Zurücksetzen ist nach wie vor die bevorzugte Methode zum Bereitstellen neuer Versionen von Anwendungen. Verwenden Sie nach Möglichkeit die Methode zum Zurücksetzen. Weitere Informationen finden Sie unter [Mage.exe (Manifest Generierung and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Entwickler von Drittanbietern und ISVs können sich für diese Funktion entscheiden, was es ihren Kunden erleichtert, ihre Anwendungen zu aktualisieren. Diese Funktion kann in den folgenden Situationen verwendet werden:  
  
- Beim Aktualisieren einer Anwendung nicht bei der ersten Installation einer Anwendung.  
  
- Wenn es nur eine Konfiguration der Anwendung auf einem Computer gibt. Wenn eine Anwendung beispielsweise so konfiguriert ist, dass sie auf zwei verschiedene Datenbanken zeigt, können Sie diese Funktion nicht verwenden.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Ausschließen von deploymentProvider aus Bereitstellungsmanifesten  
 In .NET Framework 2.0 und .NET Framework 3.0 muss jede ClickOnce-Anwendung, die `deploymentProvider` auf dem System für die Offlineverfügbarkeit installiert wird, eine im Bereitstellungsmanifest angeben. Der `deploymentProvider` wird häufig als Aktualisierungsspeicherort bezeichnet. Es ist der Speicherort, an dem ClickOnce nach Anwendungsaktualisierungen sucht. Diese Anforderung, verbunden mit der Notwendigkeit, dass Anwendungsherausgeber ihre Bereitstellungen signieren müssen, erschwerte es einem Unternehmen, eine ClickOnce-Anwendung von einem Anbieter oder einem anderen Drittanbieter zu aktualisieren. Außerdem wird es schwieriger, dieselbe Anwendung von mehreren Standorten im gleichen Netzwerk bereitzustellen.  
  
 Mit Änderungen, die an ClickOnce in .NET Framework 3.5 vorgenommen wurden, ist es für einen Drittanbieter möglich, eine ClickOnce-Anwendung für eine andere Organisation bereitzustellen, die die Anwendung dann in einem eigenen Netzwerk bereitstellen kann.  
  
 Um diese Funktion nutzen zu können, müssen Entwickler `deploymentProvider` von ClickOnce-Anwendungen aus ihren Bereitstellungsmanifesten ausschließen. Dies bedeutet, dass das `-providerUrl` Argument beim Erstellen von Bereitstellungsmanifesten mit Mage.exe ausgeschlossen wird oder ob das Textfeld **Startspeicherort** auf der Registerkarte **Anwendungsmanifest** leer bleibt, wenn Sie Bereitstellungsmanifeste mit MageUI.exe generieren.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider und Anwendungsupdates  
 Ab .NET Framework 3.5 müssen `deploymentProvider` Sie in Ihrem Bereitstellungsmanifest keine Bereitstellungsmanifest angeben, um eine ClickOnce-Anwendung für die Online- und Offlinenutzung bereitzustellen. Dies unterstützt das Szenario, in dem Sie die Bereitstellung selbst verpacken und signieren müssen, aber anderen Unternehmen die Bereitstellung der Anwendung über ihre Netzwerke ermöglichen.  
  
 Der wichtigste Punkt, der Sie `deploymentProvider` sich merken sollten, ist, dass Anwendungen, die `deploymentProvider` einen nicht ausschließen, ihren Installationsspeicherort während der Aktualisierungen nicht ändern können, bis sie ein Update, das das Tag enthält, erneut versenden.  
  
 Hier sind zwei Beispiele, um diesen Punkt zu klären. Im ersten Beispiel veröffentlichen Sie eine ClickOnce-Anwendung ohne `deploymentProvider` Tag und bitten `http://www.adatum.com/MyApplication/`Benutzer, sie von zu installieren. Wenn Sie die nächste Aktualisierung der Anwendung `http://subdomain.adatum.com/MyApplication/`von veröffentlichen möchten, können Sie dies im Bereitstellungsmanifest in nicht als "" `http://www.adatum.com/MyApplication/`bezeichnen. Sie können eines von zwei Dingen tun:  
  
- Weisen Sie die Benutzer an, die vorherige Version zu deinstallieren und die neue Version vom neuen Speicherort aus zu installieren.  
  
- Fügen Sie `http://www.adatum.com/MyApplication/` eine Aktualisierung `deploymentProvider` ein, die einen Hinweis auf `http://www.adatum.com/MyApplication/`enthält. Veröffentlichen Sie dann später `deploymentProvider` ein `http://subdomain.adatum.com/MyApplication/`weiteres Update mit verweisendem Auf.  
  
  Im zweiten Beispiel veröffentlichen Sie eine ClickOnce-Anwendung, die `deploymentProvider`angibt, und entscheiden sich dann, sie zu entfernen. Sobald die neue `deploymentProvider` Version ohne auf Clients heruntergeladen wurde, können Sie den für Updates verwendeten Pfad erst `deploymentProvider` umleiten, wenn Sie eine Version Ihrer Anwendung veröffentlichen, die wiederhergestellt wurde. Wie im ersten `deploymentProvider` Beispiel muss zunächst auf den aktuellen Aktualisierungsort und nicht auf den neuen Speicherort verweisen. Wenn Sie in diesem Fall `deploymentProvider` versuchen, `http://subdomain.adatum.com/MyApplication/`eine einzufügen, die auf verweist, schlägt die nächste Aktualisierung fehl.  
  
## <a name="creating-a-deployment"></a>Erstellen einer Bereitstellung  
 Eine Anleitung zum Erstellen von Bereitstellungen, die von verschiedenen Netzwerkstandorten bereitgestellt werden können, finden Sie unter [Exemplarische Vorgehensweise: Manuelle Bereitstellung einer ClickOnce-Anwendung, die keine erneute Signatur erfordert und Brandinginformationen beibehält.](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)  
  
## <a name="see-also"></a>Siehe auch  
 [Mage.exe (Manifest-Generierungs- und Bearbeitungstool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest Generierungs- und Bearbeitungstool, grafischer Client)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
