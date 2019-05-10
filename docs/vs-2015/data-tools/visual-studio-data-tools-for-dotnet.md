---
title: Visual Studio-Datentools für .NET | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b42617892e377dcf750e9f5cafc914759b7d0c13
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110922"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio-Datentools für .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio und .NET Framework bieten zusammen umfangreiche API und toolunterstützung für die Verbindung mit Datenbanken und Modellieren von Daten im Arbeitsspeicher zum Anzeigen der Daten in der Benutzeroberfläche.  .NET Framework-Klassen, die Datenzugriff-Funktionalität bereitstellen, werden als bezeichnet [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, zusammen mit den Daten, die in Visual Studio-Tools wurde ursprünglich entworfen, hauptsächlich als Unterstützung für relationale Datenbanken und XML. Heutzutage bieten viele NoSQL-Datenbank-Anbieter oder von Dritten, ADO.NET-Anbieter gewährleistet.  
  
 Visual Studio 2015 Update 2 enthält die neuesten Updates für [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), dem Aktivieren der Unterstützung für die neuesten Features in Azure [SQL-Datenbank](https://azure.microsoft.com/services/sql-database/) und [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). [.NET Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) ADO.NET, mit Ausnahme von Datasets und verknüpfte Typen unterstützt. Wenn Sie .NET Core Anzielen und eine Ebene objektrelationales Mapping (ORM), verwenden Sie [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).  
  
 Das folgende Diagramm zeigt eine vereinfachte Ansicht der grundlegenden Architektur:  
  
 ![ADO.NET-Architektur](../data-tools/media/raddata-ado-net-architecture-diagram.png "Raddata ADO.NET-Architekturdiagramm")  
  
 Der typische Arbeitsablauf umfasst dies:  
  
1. Installieren Sie eine Entwicklungs- oder Testdatenbank auf dem lokalen Computer. Finden Sie unter [Installieren von Datenbanksystemen, Tools und Beispielen](../data-tools/installing-database-systems-tools-and-samples.md). Wenn Sie einen Azure Data Service verwenden, ist dieser Schritt nicht erforderlich.  
  
2. Testen Sie die Verbindung mit der Datenbank (oder Dienst oder lokale Datei) in Visual Studio. Finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).  
  
3. (Optional) Verwenden Sie die Tools zum Generieren und konfigurieren ein neues Modell aus. Modelle auf Grundlage von Entity Framework sind die Empfehlung für neue Anwendungen. Das Modell, einem Sie verwenden, ist die Datenquelle, der mit die Anwendung interagiert. Das Modell befindet sich logisch zwischen der Datenbank "oder" Service "und" der Anwendung verwendet wird.  Finden Sie unter [neue Datenquellen hinzufügen](../data-tools/add-new-data-sources.md).  
  
4. Ziehen Sie die Datenquelle aus der **Datenquellen** Fenster auf einer Windows Forms, ASP.NET oder Windows Presentation Foundation-Entwurfsoberfläche, um den Code für die Datenbindung zu generieren, die die Daten für den Benutzer auf die Weise angezeigt werden, die Sie angeben. Finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
5. Hinzufügen von benutzerdefiniertem Code für Aspekte wie Geschäftsregeln, Suche und datenüberprüfung oder benutzerdefinierte Funktionalität nutzen, die die zugrunde liegenden Datenbank verfügbar macht.  
  
   Sie können überspringen Sie Schritt 3 und Programmieren eine Anwendung .NET Befehle direkt an eine Datenbank, sondern mithilfe eines Modells. In diesem Fall finden Sie hier auf die entsprechende Dokumentation: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Beachten Sie, dass Sie weiterhin verwenden können den Assistenten zur Datenquellenkonfiguration und Designern, die Datenbindung-Code generieren, wenn Sie Ihre eigenen Objekte im Arbeitsspeicher, und klicken Sie dann eine Datenbindung von UI-Steuerelemente mit diesen Objekten aufzufüllen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
- [Erstellen einer einfachen Datenanwendung mit ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
- [Neue Verbindungen hinzufügen](../data-tools/add-new-connections.md)  
  
- [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)  
  
- [Verwenden der Entity Data Model-Tools mit Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
  
- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
- [Zusätzliche Ressourcen zur Problembehandlung beim Datenzugriff](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
- [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
- [Erstellen und Verwalten von Anwendungen auf Datenebene und Datenbanken in Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
- [Zusätzliche Ressourcen zur Problembehandlung beim Datenzugriff](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
