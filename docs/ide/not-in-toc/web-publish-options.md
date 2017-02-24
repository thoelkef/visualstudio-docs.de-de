---
title: "Welche Optionen für die Veröffentlichung sind für mich geeignet? | Microsoft-Dokumentation"
ms.custom: 
ms.date: 1/31/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 85a7f3ef705d3b110ab0dc39d08d0cee235bf307
ms.openlocfilehash: 1ecb87d748a7770101bdf6e0ffe34250a36c97a8

---

# <a name="what-publishing-options-are-right-for-me"></a>Welche Optionen für die Veröffentlichung sind für mich geeignet?

Webanwendungen können aus Visual Studio direkt auf die folgenden Ziele veröffentlicht werden:

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [Dateisystem](#file-system)
- [Benutzerdefinierte Ziele (IIS, FTP usw.)](#custom-targets), darunter alle beliebigen Webserver.

Auf der Registerkarte **Veröffentlichen** können Sie ein vorhandenes Veröffentlichungsprofil auswählen, ein vorhandenes Veröffentlichungsprofil importieren oder ein neues Veröffentlichungsprofil mit den hier beschriebenen Optionen erstellen. 

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](https://azure.microsoft.com/documentation/articles/app-service-value-prop-what-is/) ermöglicht Entwicklern, schnell und ohne die Verwaltung von Infrastruktur eine Vielzahl von skalierbaren Webanwendungen und -diensten zu erstellen.

Insbesondere für Webanwendungen stellt ein App Service einen Container für eine [*Web-App*](https://azure.microsoft.com/en-us/documentation/articles/app-service-web-overview/) dar, die Ihren Vorstellungen eines herkömmlichen Webhosts stark ähnelt. Das heißt, eine Web-App stellt die erforderlichen Computingressourcen bereit, die Ihren serverseitigen Code ausführen und dem Internet zur Verfügung stellen können.

Sie bestimmen, wie viel Computingleistung einer Web-App zur Verfügung stehen, indem Sie einen [Tarif oder Plan](https://azure.microsoft.com/documentation/articles/azure-web-sites-web-hosting-plans-in-depth-overview/)) für den enthaltenden App-Dienst auswählen. Sie können mehrere Web-Apps (und andere App-Typen) ohne Tarifänderung denselben App Service nutzen lassen. Sie können z.B. Entwicklungs-, Staging- und Produktions-Web-Apps gemeinsam im selben App Service hosten. 

Ein App Service wird auf in der Cloud gehosteten virtuellen Computern in Azure ausgeführt, aber diese virtuellen Maschinen werden für Sie verwaltet. Jeder Web-App in einem App Service wird eine eindeutige „*. azurewebsites.net“-URL zugeordnet. Alle Tarife (außer „kostenlos“) ermöglichen zudem, dass Sie der Website benutzerdefinierte Domänennamen zuweisen.  

### <a name="when-to-choose-azure-app-service"></a>Wann sollten Sie Azure App Service wählen?

- Sie möchten eine Webanwendung bereitstellen, auf die über das Internet zugegriffen werden kann.
- Sie möchten Ihre Webanwendung automatisch entsprechend Ihrem Bedarf skalieren, ohne sie erneut bereitstellen zu müssen.
- Sie möchten keine Serverinfrastruktur (einschließlich aller Softwareupdates) verwalten.
- Auf den Servern, auf denen Ihre Anwendung gehostet wird, sind keine Anpassungen auf Computerebene erforderlich.


> Wenn Sie Azure App Service in Ihrem eigenen Datencenter oder anderen lokalen Computern verwenden möchten, können Sie dazu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) verwenden.


## <a name="azure-virtual-machines"></a>Azure Virtual Machines

Mit [Azure Virtual Machines (VMs)](https://azure.microsoft.com/documentation/services/virtual-machines/) können Sie eine beliebige Anzahl von Computingressourcen in der Cloud erstellen und verwalten. Indem Sie die Verantwortung für die gesamte Software und alle Updates auf den VMs übernehmen, können Sie diese wie gewünscht dem Bedarf Ihrer Webanwendung anpassen. Sie können auch direkt über den Remotedesktop auf die Server zugreifen, und jeder behält, sofern gewünscht, die ihm zugewiesene IP-Adresse bei.

Beim Skalieren einer Webanwendung, die auf virtuellen Computern gehostet wird, werden zusätzliche VMs entsprechend dem Bedarf sowie die erforderliche Software bereitgestellt. Diese zusätzliche Kontrollebene ermöglicht Ihnen, in verschiedenen Regionen weltweit unterschiedliche Skalierungen vorzunehmen. Wenn Ihre Anwendung beispielsweise von Mitarbeitern in einer Vielzahl von Zweigstellen eingesetzt wird, können Sie Ihre virtuellen Computer entsprechend der Anzahl der Mitarbeiter in diesen Regionen skalieren und damit potenziell Kosten senken. 

Weitere Informationen finden Sie in dem [detaillierten Vergleich](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) zwischen Azure App Service, Azure Virtual Machines und anderen Azure-Diensten, die Sie als Bereitstellungsziel mithilfe der Option „Benutzerdefiniert“ in Visual Studio verwenden können.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Wann sollten Sie Azure Virtual Machines wählen?

- Sie möchten eine über das Internet zugängliche Webanwendung mit vollständiger Kontrolle über die Lebensdauer der zugewiesenen IP-Adressen bereitstellen.
- Sie benötigen auf den Servern Anpassungen auf Computerebene, einschließlich Software, wie z.B. ein spezielles Datenbanksysten, bestimmte Netzwerkkonfigurationen, Datenträgerpartitionen und so weiter.
- Sie benötigen hochgradige Kontrolle über die Skalierung Ihrer Webanwendung.
- Sie benötigen aus anderen Gründen direkten Zugriff auf die Server, auf denen Ihre Anwendung gehostet wird.

> Wenn Sie Azure Virtual Machines in Ihrem eigenen Datencenter oder anderen lokalen Computern verwenden möchten, können Sie dazu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) verwenden.


## <a name="file-system"></a>Dateisystem

Bereitstellung im Dateisystem bedeutet einfach, dass Sie die Dateien Ihrer Webanwendung in einen bestimmten Ordner auf Ihrem eigenen Computer kopieren. Dies erfolgt meistens zu Testzwecken oder zum Bereitstellen der Anwendung für die Verwendung durch eine begrenzte Anzahl von Personen, wenn auf dem Computer auch ein Webserver ausgeführt wird. Wird der Zielordner in einem Netzwerk freigegeben, können die Webanwendungsdateien durch das Bereitstellen im Dateisystem auch für andere Personen verfügbar gemacht werden, die diese dann auf bestimmten Servern bereitstellen können.  

Alle lokalen Computer, auf denen ein Webserver ausgeführt wird, können die Anwendung, abhängig von Konfiguration und Netzwerkverbindungen, über das Internet oder ein Intranet verfügbar machen. (Wenn Sie einen Computer direkt mit dem Internet verbinden, müssen Sie ihn besonders vor externen Sicherheitsrisiken schützen.) Da Sie diese Computer verwalten, haben Sie vollständige Kontrolle über die Software- und Hardwarekonfigurationen. 

Beachten Sie Folgendes: Wenn die Verwendung von Clouddiensten wie Azure App Service oder Azure Virtual Machines aus irgendeinem Grund (z.B. Computerzugriff) nicht möglich ist, können Sie [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) in Ihrem eigenen Datencenter verwenden. Azure Stack ermöglicht die lokale Verwaltung und Verwendung von Computerressourcen über Azure App Service und Azure Virtual Machines.  

### <a name="when-to-choose-file-system-deployment"></a>Wann sollten Sie die Bereitstellung im Dateisystem wählen?

- Sie müssen die Anwendung nur auf einer Dateifreigabe bereitstellen. Von dort werden sie von anderen Benutzern auf verschiedenen Servern bereitgestellt.
- Sie benötigen nur eine lokale Testbereitstellung.
- Sie möchten Anwendungsdateien einzeln untersuchen und möglicherweise ändern, bevor sie auf ein anderes Bereitstellungsziel gesendet werden.



## <a name="custom-targets"></a>Benutzerdefinierte Ziele

Ein benutzerdefiniertes Ziel ermöglicht Ihnen die Bereitstellung Ihrer Webanwendung auf einem anderen Ziel als Azure App Service, Azure Virtual Machines oder dem lokalen Dateisystem. Sie können die Webanwendung in einem Dateisystem oder auf einem anderen Server (Internet oder Intranet) bereitstellen, auf das bzw. den Sie Zugriff haben, einschließlich Ziele in anderen Clouddiensten. Es funktioniert mit Web Deploy (Dateien oder ZIP) und FTP. 

Wenn Sie ein benutzerdefiniertes Ziel auswählen, fordert Visual Studio Sie auf, einen Profilnamen anzugeben, und erfasst anschließend zusätzliche Informationen zur **Verbindung**, einschließlich Zielserver oder Speicherort, Standortnamen und Anmeldeinformationen. Sie können auch bestimmte Verhaltensweisen über die Registerkarte **Einstellungen** steuern, beispielsweise welche Konfiguration bereitgestellt wird, ob vorhandene Dateien aus dem Ziel entfernt werden, ob während der Veröffentlichung eine Vorkompilierung erfolgt und ob Dateien im Ordner „App_Data“ von der Bereitstellung ausgeschlossen werden. 

Sie können in Visual Studio beliebig viele benutzerdefinierte Bereitstellungsprofile erstellen, wodurch Sie bei Bedarf Profile mit leicht unterschiedlichen Einstellungen verwalten können.

### <a name="when-to-choose-custom-deployment"></a>Wann sollten Sie die benutzerdefinierte Bereitstellung wählen?

- Sie verwenden Clouddienste in einer anderen als einer auf Azure-Bereitstellung, auf die über URLs zugegriffen werden kann.
- Sie möchten eine Bereitstellung mit anderen als den in Visual Studio verwendeten oder den direkt mit Ihren Azure-Konten verknüpften Anmeldeinformationen durchführen.
- Sie möchten bei jeder Bereitstellung Dateien vom Ziel löschen. 




<!--HONumber=Feb17_HO4-->


