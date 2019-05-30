---
title: Übersicht über die Bereitstellung | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 06/22/2018
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7c322b960360231c2e8a1d2aa1a9920bbcf5521
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263301"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Übersicht über die Bereitstellung in Visual Studio

Wenn Sie eine Anwendung, einen Dienst oder eine Komponente bereitstellen, verteilen Sie diese für die Installation auf anderen Computern, Geräten, Servern oder in der Cloud. Wählen Sie die entsprechende Methode für den Typ der Bereitstellung in Visual Studio aus, den Sie benötigen.

Für viele gängige App-Typen können Sie Ihre App direkt über den Projektmappen-Explorer in Visual Studio bereitstellen. Einen schnellen Überblick über diese Funktion finden Sie unter [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md).

![Auswählen einer Veröffentlichungsoption](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Welche Optionen für die Veröffentlichung sind für mich geeignet?

Apps können aus Visual Studio direkt auf die folgenden Ziele veröffentlicht werden:

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [Dateisystem](#file-system)
- [Benutzerdefinierte Ziele (IIS, FTP usw.)](#custom-targets-iis-ftp), darunter alle beliebigen Webserver.

Auf der Registerkarte **Veröffentlichen** können Sie ein vorhandenes Veröffentlichungsprofil auswählen, ein vorhandenes Veröffentlichungsprofil importieren oder ein neues Veröffentlichungsprofil mit den hier beschriebenen Optionen erstellen. Einen Überblick über Veröffentlichungsoptionen in der IDE für unterschiedliche App-Typen finden Sie unter [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) und [App Service unter Linux](/azure/app-service/containers/app-service-linux-intro) ermöglichen Entwicklern, schnell und ohne die Verwaltung von Infrastruktur eine Vielzahl von skalierbaren Webanwendungen und -diensten zu erstellen.

Sie bestimmen, wie viel Computingleistung dem App Service zur Verfügung stehen, indem Sie einen [Tarif oder Plan](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) für den enthaltenden App Service auswählen. Sie können mehrere Web-Apps (und andere App-Typen) ohne Tarifänderung den gleichen App Service nutzen lassen. Sie können z.B. Entwicklungs-, Staging- und Produktions-Web-Apps gemeinsam im selben App Service hosten.

Ein App Service wird auf in der Cloud gehosteten virtuellen Computern in Azure ausgeführt, aber diese virtuellen Maschinen werden für Sie verwaltet. Jeder App in einem App Service wird eine eindeutige „\*. azurewebsites.net“-URL zugeordnet. Alle Tarife (außer „kostenlos“) ermöglichen, dass Sie der Website benutzerdefinierte Domänennamen zuweisen.

### <a name="when-to-choose-azure-app-service"></a>Wann sollten Sie Azure App Service wählen?

- Sie möchten eine Webanwendung bereitstellen, auf die über das Internet zugegriffen werden kann.
- Sie möchten Ihre Webanwendung automatisch entsprechend Ihrem Bedarf skalieren, ohne sie erneut bereitstellen zu müssen.
- Sie möchten keine Serverinfrastruktur (einschließlich Softwareupdates) verwalten.
- Auf den Servern, auf denen Ihre Anwendung gehostet wird, sind keine Anpassungen auf Computerebene erforderlich.

> Wenn Sie Azure App Service in Ihrem eigenen Datencenter oder anderen lokalen Computern verwenden möchten, können Sie dazu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) verwenden.

Weitere Informationen zur Veröffentlichung in App Service finden Sie in den Schnellstarts zum [Veröffentlichen von Web-Apps in Azure App Service](quickstart-deploy-to-azure.md) und [Veröffentlichen einer ASP.NET Core-App unter Linux](quickstart-deploy-to-linux.md).

## <a name="azure-virtual-machines"></a>Azure Virtual Machines

Mit [Azure Virtual Machines (VMs)](https://azure.microsoft.com/documentation/services/virtual-machines/) können Sie eine beliebige Anzahl von Computingressourcen in der Cloud erstellen und verwalten. Indem Sie die Verantwortung für die gesamte Software und alle Updates auf den VMs übernehmen, können Sie diese wie gewünscht dem Bedarf Ihrer App anpassen. Sie können direkt über den Remotedesktop auf die VMs zugreifen, und jeder behält, sofern gewünscht, die ihm zugewiesene IP-Adresse bei.

Beim Skalieren einer App, die auf virtuellen Computern gehostet wird, werden zusätzliche VMs entsprechend dem Bedarf sowie die erforderliche Software bereitgestellt. Diese zusätzliche Kontrollebene ermöglicht Ihnen, in verschiedenen Regionen weltweit unterschiedliche Skalierungen vorzunehmen. Wenn Ihre Anwendung beispielsweise von Mitarbeitern in einer Vielzahl von Zweigstellen eingesetzt wird, können Sie Ihre virtuellen Computer entsprechend der Anzahl der Mitarbeiter in diesen Regionen skalieren und damit potenziell Kosten senken.

Weitere Informationen finden Sie in dem [detaillierten Vergleich](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) zwischen Azure App Service, Azure Virtual Machines und anderen Azure-Diensten, die Sie als Bereitstellungsziel mithilfe der Option „Benutzerdefiniert“ in Visual Studio verwenden können.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Wann sollten Sie Azure Virtual Machines wählen?

- Sie möchten eine über das Internet zugängliche Webanwendung mit vollständiger Kontrolle über die Lebensdauer der zugewiesenen IP-Adressen bereitstellen.
- Sie benötigen auf den Servern Anpassungen auf Computerebene, einschließlich Software, wie z.B. ein spezielles Datenbanksysten, bestimmte Netzwerkkonfigurationen, Datenträgerpartitionen und so weiter.
- Sie benötigen hochgradige Kontrolle über die Skalierung Ihrer Webanwendung.
- Sie benötigen aus anderen Gründen direkten Zugriff auf die Server, auf denen Ihre Anwendung gehostet wird.

> Wenn Sie Azure Virtual Machines in Ihrem eigenen Datencenter oder anderen lokalen Computern verwenden möchten, können Sie dazu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) verwenden.

## <a name="file-system"></a>Dateisystem

Bereitstellung im Dateisystem bedeutet einfach, dass Sie die Dateien Ihrer App in einen bestimmten Ordner auf Ihrem eigenen Computer kopieren. Dies erfolgt meistens zu Testzwecken oder zum Bereitstellen der Anwendung für die Verwendung durch eine begrenzte Anzahl von Personen, wenn auf dem Computer auch ein Server ausgeführt wird. Wird der Zielordner in einem Netzwerk freigegeben, können die Webanwendungsdateien durch das Bereitstellen im Dateisystem für andere Personen verfügbar gemacht werden, die diese dann auf bestimmten Servern bereitstellen können.

Alle lokalen Computer, auf denen ein Server ausgeführt wird, können die App, abhängig von Konfiguration und Netzwerkverbindungen, über das Internet oder ein Intranet zur Verfügung stellen. (Wenn Sie einen Computer direkt mit dem Internet verbinden, müssen Sie ihn besonders vor externen Sicherheitsrisiken schützen.) Da Sie diese Computer verwalten, haben Sie vollständige Kontrolle über die Software- und Hardwarekonfigurationen.

Beachten Sie Folgendes: Wenn die Verwendung von Clouddiensten wie Azure App Service oder Azure Virtual Machines aus irgendeinem Grund (z.B. Computerzugriff) nicht möglich ist, können Sie [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) in Ihrem eigenen Datencenter verwenden. Azure Stack ermöglicht die lokale Verwaltung und Verwendung von Computerressourcen über Azure App Service und Azure Virtual Machines.

### <a name="when-to-choose-file-system-deployment"></a>Wann sollten Sie die Bereitstellung im Dateisystem wählen?

- Sie müssen die Anwendung nur auf einer Dateifreigabe bereitstellen. Von dort werden sie von anderen Benutzern auf verschiedenen Servern bereitgestellt.
- Sie benötigen nur eine lokale Testbereitstellung.
- Sie möchten Anwendungsdateien einzeln untersuchen und möglicherweise ändern, bevor sie auf ein anderes Bereitstellungsziel gesendet werden.

Weitere Informationen finden Sie unter [Quickstart – Deploy to a local folder (Schnellstart: Bereitstellen einer App in einem lokalen Ordner)](quickstart-deploy-to-local-folder.md).

## <a name="custom-targets-iis-ftp"></a>Benutzerdefinierte Ziele (IIS, FTP)

Ein benutzerdefiniertes Ziel ermöglicht Ihnen die Bereitstellung Ihrer App auf einem anderen Ziel als Azure App Service, Azure Virtual Machines oder dem lokalen Dateisystem. Sie können die Webanwendung in einem Dateisystem oder auf einem anderen Server (Internet oder Intranet) bereitstellen, auf das bzw. den Sie Zugriff haben, einschließlich Ziele in anderen Clouddiensten. Es funktioniert mit Web Deploy (Dateien oder ZIP) und FTP.

Wenn Sie ein benutzerdefiniertes Ziel auswählen, fordert Visual Studio Sie auf, einen Profilnamen anzugeben, und erfasst anschließend zusätzliche Informationen zur **Verbindung**, einschließlich Zielserver oder Speicherort, Standortnamen und Anmeldeinformationen. Sie können folgendes Verhalten auf der Registerkarte **Einstellungen** steuern:

- Die Konfiguration, die Sie bereitstellen möchten.
- Ob vorhandene Dateien aus dem Ziel entfernt werden.
- Ob während der Veröffentlichung vorkompiliert wird.
- Ob Dateien im Ordner „App_Data“ von der Bereitstellung ausgeschlossen sind.

Sie können in Visual Studio beliebig viele benutzerdefinierte Bereitstellungsprofile erstellen, wodurch Sie Profile mit unterschiedlichen Einstellungen verwalten können.

### <a name="when-to-choose-custom-deployment"></a>Wann sollten Sie die benutzerdefinierte Bereitstellung wählen?

- Sie verwenden Clouddienste auf einem anderen Anbieter als Azure, auf den über URLs zugegriffen werden kann.
- Sie möchten eine Bereitstellung mit anderen als den in Visual Studio verwendeten oder den direkt mit Ihren Azure-Konten verknüpften Anmeldeinformationen durchführen.
- Sie möchten bei jeder Bereitstellung Dateien vom Ziel löschen.

Weitere Informationen finden Sie unter [Quickstart – Deploy to a local folder (Schnellstart: Bereitstellen einer App in einem lokalen Ordner)](quickstart-deploy-to-a-web-site.md).

## <a name="next-steps"></a>Nächste Schritte

Tutorials:

- [Bereitstellen von .NET Core-Apps mit Visual Studio](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Veröffentlichen einer ASP.NET Core-App in Azure mit Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Bereitstellung in Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Deploy UWP apps (Bereitstellen von UWP-Apps)](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publish a Node.js app to Azure using Web Deploy (Bereitstellen einer Node.js-App in Azure mithilfe von Web Deploy)](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Veröffentlichen einer Python-App in Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
