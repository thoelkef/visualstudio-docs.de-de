---
title: ClickOnce-Apps bereitstellen, ohne erneut zu signieren
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395325"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>ClickOnce-Anwendungen zum Testen und Testen von Produktionsservern ohne Zurückweisen bereitstellen
In diesem Artikel wird eine Funktion von ClickOnce beschrieben, die in der .NET Framework-Version 3.5 eingeführt wurde und die Bereitstellung von ClickOnce-Anwendungen von mehreren Netzwerkstandorten aus ermöglicht, ohne die ClickOnce-Manifeste neu signieren oder ändern zu müssen.

> [!NOTE]
> Das Zurücksetzen ist nach wie vor die bevorzugte Methode zum Bereitstellen neuer Versionen von Anwendungen. Verwenden Sie nach Möglichkeit die Methode zum Zurücksetzen. Weitere Informationen finden Sie unter [ *Mage.exe* (Manifest Generierung and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Entwickler von Drittanbietern und ISVs können sich für diese Funktion entscheiden, was es ihren Kunden erleichtert, ihre Anwendungen zu aktualisieren. Diese Funktion kann in den folgenden Situationen verwendet werden:

- Beim Aktualisieren einer Anwendung nicht für die erste Installation einer Anwendung.

- Wenn es nur eine Konfiguration der Anwendung auf einem Computer gibt. Wenn eine Anwendung beispielsweise so konfiguriert ist, dass sie auf zwei verschiedene Datenbanken zeigt, können Sie diese Funktion nicht verwenden.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>DeploymentProvider von Bereitstellungsmanifesten ausschließen
 In .NET Framework 2.0 und .NET Framework 3.0 muss jede ClickOnce-Anwendung, die `deploymentProvider` auf dem System für die Offlineverfügbarkeit installiert wird, eine im Bereitstellungsmanifest auflisten. Der `deploymentProvider` wird häufig als Aktualisierungsspeicherort bezeichnet. Es ist der Speicherort, an dem ClickOnce nach Anwendungsaktualisierungen sucht. Diese Anforderung und die Notwendigkeit, dass Anwendungsherausgeber ihre Bereitstellungen signieren müssen, erschwerten es einem Unternehmen, eine ClickOnce-Anwendung von einem Anbieter oder einem anderen Drittanbieter zu aktualisieren. Außerdem wird es schwieriger, dieselbe Anwendung von mehreren Standorten im gleichen Netzwerk bereitzustellen.

 Mit Änderungen, die an ClickOnce in .NET Framework 3.5 vorgenommen wurden, ist es für einen Drittanbieter möglich, eine ClickOnce-Anwendung für eine andere Organisation bereitzustellen, die die Anwendung dann in einem eigenen Netzwerk bereitstellen kann.

 Um diese Funktion nutzen zu können, müssen Entwickler `deploymentProvider` von ClickOnce-Anwendungen aus ihren Bereitstellungsmanifesten ausschließen. Diese Anforderung bedeutet, dass `-providerUrl` Sie das Argument ausschließen müssen, wenn Sie Bereitstellungsmanifeste mit Mage.exe erstellen. Wenn Sie Bereitstellungsmanifeste mit MageUI.exe generieren, müssen Sie auch sicherstellen, dass das Textfeld **Startspeicherort** auf der Registerkarte **Anwendungsmanifest** leer bleibt.

## <a name="deploymentprovider-and-application-updates"></a>DeploymentAnbieter- und Anwendungsupdates
 Ab .NET Framework 3.5 müssen `deploymentProvider` Sie in Ihrem Bereitstellungsmanifest keine Bereitstellungsmanifest angeben, um eine ClickOnce-Anwendung für die Online- und Offlinenutzung bereitzustellen. Diese Änderung unterstützt das Szenario, in dem Sie die Bereitstellung selbst verpacken und signieren müssen, aber anderen Unternehmen die Bereitstellung der Anwendung über ihre Netzwerke ermöglichen.

 Der wichtige Punkt, an den `deploymentProvider` Sie sich erinnern sollten, ist, dass Anwendungen, `deploymentProvider` die einen nicht ausschließen, ihren Installationsspeicherort während der Aktualisierungen nicht ändern können, bis sie ein Update versenden, das das Tag erneut enthält.

 Hier sind zwei Beispiele, um diesen Punkt zu klären. Im ersten Beispiel veröffentlichen Sie eine ClickOnce-Anwendung ohne `deploymentProvider` Tag und bitten `http://www.adatum.com/MyApplication/`Benutzer, sie von zu installieren. Wenn Sie die nächste Aktualisierung der Anwendung `http://subdomain.adatum.com/MyApplication/`von veröffentlichen möchten, können Sie dies im Bereitstellungsmanifest in nicht als "" `http://www.adatum.com/MyApplication/`bezeichnen. Sie können eines von zwei Dingen tun:

- Weisen Sie die Benutzer an, die vorherige Version zu deinstallieren und die neue Version vom neuen Speicherort aus zu installieren.

- Fügen Sie `http://www.adatum.com/MyApplication/` eine Aktualisierung `deploymentProvider` ein, die einen Hinweis auf `http://www.adatum.com/MyApplication/`enthält. Veröffentlichen Sie dann später `deploymentProvider` ein `http://subdomain.adatum.com/MyApplication/`weiteres Update mit verweisendem Auf.

  Im zweiten Beispiel veröffentlichen Sie eine ClickOnce-Anwendung, die `deploymentProvider`angibt, und entscheiden sich dann, sie zu entfernen. Sobald die neue `deploymentProvider` Version ohne auf Clients heruntergeladen wurde, können Sie den für Updates `deploymentProvider` verwendeten Pfad erst dann umleiten, wenn Sie eine Version Ihrer Anwendung freigeben, die wiederhergestellt wurde. Wie im ersten `deploymentProvider` Beispiel muss zunächst auf den aktuellen Aktualisierungsort und nicht auf den neuen Speicherort verweisen. Wenn Sie in diesem Fall `deploymentProvider` versuchen, `http://subdomain.adatum.com/MyApplication/`eine einzufügen, die auf verweist, schlägt die nächste Aktualisierung fehl.

## <a name="create-a-deployment"></a>Erstellen einer Bereitstellung
 Eine Anleitung zum Erstellen von Bereitstellungen, die von verschiedenen Netzwerkstandorten bereitgestellt werden können, finden Sie unter [Exemplarische Vorgehensweise: Manuelle Bereitstellung einer ClickOnce-Anwendung, die keine neu signieren muss und die Brandinginformationen beibehält.](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)

## <a name="see-also"></a>Siehe auch
- [*Mage.exe* (Manifest-Generierungs- und Bearbeitungstool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Manifest Generierungs- und Bearbeitungstool, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
