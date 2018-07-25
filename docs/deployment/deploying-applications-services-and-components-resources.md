---
title: Übersicht über die Bereitstellung – Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d5b15af932f8d796a27dfc060128617816b9234
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232172"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Übersicht über die Bereitstellung in Visual Studio

Wenn Sie eine Anwendung, einen Dienst oder eine Komponente bereitstellen, verteilen Sie diese für die Installation auf anderen Computern, Geräten, Servern oder in der Cloud. Wählen Sie die entsprechende Methode für den Typ der Bereitstellung in Visual Studio aus, den Sie benötigen.

Für viele allgemeine app-Typen können Sie Ihre Anwendung direkt aus dem Projektmappen-Explorer in Visual Studio bereitstellen. Einen kurzen Überblick über diese Funktion finden Sie unter [ein erster Blick auf die Bereitstellung](../deployment/deploying-applications-services-and-components.md).

![Wählen Sie eine Veröffentlichungsoption](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Welche Optionen für die Veröffentlichung sind für mich geeignet?

Von können Anwendungen in Visual Studio direkt auf die folgenden Ziele veröffentlicht werden:

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [Dateisystem](#file-system)
- [Benutzerdefinierte Ziele (IIS, FTP usw.)](#custom-targets), darunter alle beliebigen Webserver.

Auf der Registerkarte **Veröffentlichen** können Sie ein vorhandenes Veröffentlichungsprofil auswählen, ein vorhandenes Veröffentlichungsprofil importieren oder ein neues Veröffentlichungsprofil mit den hier beschriebenen Optionen erstellen. Einen Überblick über Veröffentlichungsoptionen in der IDE für unterschiedliche App-Typen finden Sie unter [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) und [App Service unter Linux](/azure/app-service/containers/app-service-linux-intro) ermöglicht es Entwicklern, schnell eine Vielzahl von skalierbaren Webanwendungen und-Dienste erstellen, ohne die Verwaltung von Infrastruktur.

Sie bestimmen, wie viel Computingleistung einer App Service durch Auswahl wurde ein [Tarif oder Plan](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) für den enthaltenden App-Dienst. Sie haben mehrere Web-apps (und andere app-Typen) gemeinsam im selben App Service ohne Ändern des Tarifs nutzen. Sie können z.B. Entwicklungs-, Staging- und Produktions-Web-apps auf den gleichen App Service hosten.

Ein App Service wird auf in der Cloud gehosteten virtuellen Computern in Azure ausgeführt, aber diese virtuellen Maschinen werden für Sie verwaltet. Jede app in App Service wird eine eindeutige zugewiesen \*. AZUREWEBSITES.NET"-URL; alle Tarife außer Free können von der Website benutzerdefinierte Domänennamen zuweisen.

### <a name="when-to-choose-azure-app-service"></a>Wann sollten Sie Azure App Service wählen?

- Sie möchten eine Webanwendung bereitstellen, auf die über das Internet zugegriffen werden kann.
- Sie möchten Ihre Webanwendung automatisch entsprechend Ihrem Bedarf skalieren, ohne sie erneut bereitstellen zu müssen.
- Sie möchten keine Serverinfrastruktur (einschließlich Softwareupdates) verwalten.
- Auf den Servern, auf denen Ihre Anwendung gehostet wird, sind keine Anpassungen auf Computerebene erforderlich.

> Wenn Sie Azure App Service in Ihrem eigenen Datencenter oder anderen lokalen Computern verwenden möchten, können Sie dazu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) verwenden.

Weitere Informationen zum Veröffentlichen in App Service finden Sie unter [-Schnellstart – Veröffentlichen in Azure App Service](quickstart-deploy-to-azure.md) und [-Schnellstart – Veröffentlichen von ASP.NET Core, Linux](quickstart-deploy-to-linux.md).

## <a name="azure-virtual-machines"></a>Azure Virtual Machines

Mit [Azure Virtual Machines (VMs)](https://azure.microsoft.com/documentation/services/virtual-machines/) können Sie eine beliebige Anzahl von Computingressourcen in der Cloud erstellen und verwalten. Durch die Verantwortung für die gesamte Software und Updates auf den VMs, können Sie diese anpassen wie gewünscht als von der Anwendung benötigt. Sie können direkt über den Remotedesktop auf die VMs zugreifen, und jeder behält, sofern gewünscht, die ihm zugewiesene IP-Adresse bei.

Skalieren einer Anwendung, die auf virtuellen Computern gehostet wird, umfasst zusätzliche VMs entsprechend bei Bedarf, und klicken Sie dann die erforderliche Software bereitgestellt. Diese zusätzliche Kontrollebene ermöglicht Ihnen, in verschiedenen Regionen weltweit unterschiedliche Skalierungen vorzunehmen. Wenn Ihre Anwendung beispielsweise von Mitarbeitern in einer Vielzahl von Zweigstellen eingesetzt wird, können Sie Ihre virtuellen Computer entsprechend der Anzahl der Mitarbeiter in diesen Regionen skalieren und damit potenziell Kosten senken.

Weitere Informationen finden Sie in dem [detaillierten Vergleich](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) zwischen Azure App Service, Azure Virtual Machines und anderen Azure-Diensten, die Sie als Bereitstellungsziel mithilfe der Option „Benutzerdefiniert“ in Visual Studio verwenden können.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Wann sollten Sie Azure Virtual Machines wählen?

- Sie möchten eine über das Internet zugängliche Webanwendung mit vollständiger Kontrolle über die Lebensdauer der zugewiesenen IP-Adressen bereitstellen.
- Sie benötigen auf den Servern Anpassungen auf Computerebene, einschließlich Software, wie z.B. ein spezielles Datenbanksysten, bestimmte Netzwerkkonfigurationen, Datenträgerpartitionen und so weiter.
- Sie benötigen hochgradige Kontrolle über die Skalierung Ihrer Webanwendung.
- Sie benötigen aus anderen Gründen direkten Zugriff auf die Server, auf denen Ihre Anwendung gehostet wird.

> Wenn Sie Azure Virtual Machines in Ihrem eigenen Datencenter oder anderen lokalen Computern verwenden möchten, können Sie dazu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) verwenden.

## <a name="file-system"></a>Dateisystem

Bereitstellen im Dateisystem bedeutet einfach den Dateien Ihrer Anwendung in einem angegebenen Ordner auf Ihrem eigenen Computer kopieren. Dies wird am häufigsten verwendet, zu Testzwecken oder zum Bereitstellen von der Anwendung für die Verwendung durch eine begrenzte Anzahl von Personen, wenn der Computer auch einen Server ausgeführt wird. Wird der Zielordner in einem Netzwerk freigegeben, können die Webanwendungsdateien durch das Bereitstellen im Dateisystem für andere Personen verfügbar gemacht werden, die diese dann auf bestimmten Servern bereitstellen können.

Alle lokalen Computer, die auf einem Server ausgeführt werden können verfügbar machen, Ihre Anwendung über das Internet oder ein Intranet, je nachdem, wie es konfiguriert ist und die Netzwerke, die mit denen sie verbunden ist. (Wenn Sie einen Computer direkt mit dem Internet verbinden, müssen Sie ihn besonders vor externen Sicherheitsrisiken schützen.) Da Sie diese Computer verwalten, haben Sie vollständige Kontrolle über die Software- und Hardwarekonfigurationen.

Beachten Sie Folgendes: Wenn die Verwendung von Clouddiensten wie Azure App Service oder Azure Virtual Machines aus irgendeinem Grund (z.B. Computerzugriff) nicht möglich ist, können Sie [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) in Ihrem eigenen Datencenter verwenden. Azure Stack ermöglicht die lokale Verwaltung und Verwendung von Computerressourcen über Azure App Service und Azure Virtual Machines.

### <a name="when-to-choose-file-system-deployment"></a>Wann sollten Sie die Bereitstellung im Dateisystem wählen?

- Sie müssen die Anwendung nur auf einer Dateifreigabe bereitstellen. Von dort werden sie von anderen Benutzern auf verschiedenen Servern bereitgestellt.
- Sie benötigen nur eine lokale Testbereitstellung.
- Sie möchten Anwendungsdateien einzeln untersuchen und möglicherweise ändern, bevor sie auf ein anderes Bereitstellungsziel gesendet werden.

Weitere Informationen finden Sie unter [-Schnellstart – Bereitstellen in einem lokalen Ordner](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Benutzerdefinierte Ziele (IIS, FTP)

Ein benutzerdefiniertes Ziel ermöglicht Ihnen die Bereitstellung Ihrer Anwendung in ein anderes Ziel als Azure App Service, Azure Virtual Machines oder das lokale Dateisystem. Sie können die Webanwendung in einem Dateisystem oder auf einem anderen Server (Internet oder Intranet) bereitstellen, auf das bzw. den Sie Zugriff haben, einschließlich Ziele in anderen Clouddiensten. Es funktioniert mit Web Deploy (Dateien oder ZIP) und FTP.

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

Weitere Informationen finden Sie unter [-Schnellstart – Bereitstellen in einer Website](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Nächste Schritte

Tutorials:

- [Bereitstellen einer .NET Core-Anwendung mit dem Tool "Veröffentlichen"](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Veröffentlichen einer ASP.NET Core-app in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Bereitstellung in Visual C++](/cpp/ide/deployment-in-visual-cpp)
- [Bereitstellen von UWP-apps](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Veröffentlichen Sie eine Node.js-app in Azure mithilfe von Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Veröffentlichen einer Python-app in Azure App Service](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
