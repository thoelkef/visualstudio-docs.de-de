---
title: Visual Studio-Daten Tools für .net | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670100"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio-Datentools für .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio und die .NET Framework bieten eine umfassende Unterstützung für APIs und Tools zum Herstellen einer Verbindung mit Datenbanken, zum Modellieren von Daten im Arbeitsspeicher und zum Anzeigen der Daten auf der Benutzeroberfläche.  Die .NET Framework-Klassen, die Datenzugriffs Funktionen bereitstellen, werden als [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx)bezeichnet. ADO.net, zusammen mit den Daten Tools in Visual Studio, wurde ursprünglich hauptsächlich zur Unterstützung von relationalen Datenbanken und XML entwickelt. Heutzutage bieten viele nosql-Datenbankanbieter oder Drittanbieter ADO.NET-Anbieter an.

 Visual Studio 2015 Update 2 enthält die neuesten Updates von            [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), die die Unterstützung für die neuesten Features in Azure [SQL-Datenbank](https://azure.microsoft.com/services/sql-database/) und [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016)ermöglichen. [.Net Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) unterstützt ADO.net, mit Ausnahme von Datasets und zugehörigen Typen. Wenn Sie .net Core als Ziel verwenden und eine ORM-Ebene (Object-Relational Mapping) benötigen, verwenden Sie [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).

 Das folgende Diagramm zeigt eine vereinfachte Ansicht der grundlegenden Architektur:

 ![ADO.NET-Architektur](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata ADO.NET Architektur Diagramm")

 Der typische Workflow lautet wie folgt:

1. Installieren Sie eine Entwicklungs-oder Testdatenbank auf dem lokalen Computer. Weitere Informationen finden Sie unter [Installieren von Datenbanksystemen, Tools und Beispielen](../data-tools/installing-database-systems-tools-and-samples.md). Wenn Sie einen Azure-Datendienst verwenden, ist dieser Schritt nicht erforderlich.

2. Testen Sie die Verbindung mit der Datenbank (oder dem Dienst oder der lokalen Datei) in Visual Studio. Siehe [Hinzufügen neuer Verbindungen](../data-tools/add-new-connections.md).

3. Optionale Verwenden Sie die-Tools, um ein neues Modell zu generieren und zu konfigurieren. Modelle, die auf Entity Framework basieren, sind die Standard Empfehlung für neue Anwendungen. Das Modell, das Sie verwenden, ist die Datenquelle, mit der die Anwendung interagiert. Das Modell befindet sich logisch zwischen der Datenbank oder dem Dienst und der Anwendung.  Siehe [Hinzufügen neuer Datenquellen](../data-tools/add-new-data-sources.md).

4. Ziehen Sie die Datenquelle aus dem **Datenquellen** Fenster auf eine Windows Forms-, ASP.net-oder Windows Presentation Foundation-Entwurfs Oberfläche, um den Daten Bindungs Code zu generieren, der die Daten für den Benutzer auf die von Ihnen angegebene Weise anzeigt. Siehe [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Fügen Sie benutzerdefinierten Code für Dinge wie Geschäftsregeln, Suche und Datenvalidierung hinzu, oder verwenden Sie benutzerdefinierte Funktionen, die von der zugrunde liegenden Datenbank verfügbar gemacht werden.

   Sie können Schritt 3 überspringen und eine .NET-Anwendung programmieren, um Befehle direkt an eine Datenbank auszugeben, anstatt ein Modell zu verwenden. In diesem Fall finden Sie hier auf die entsprechende Dokumentation: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Beachten Sie, dass Sie den Assistenten zum Konfigurieren von Datenquellen und Designer weiterhin verwenden können, um Daten Bindungs Code zu generieren, wenn Sie Ihre eigenen Objekte im Arbeitsspeicher auffüllen und anschließend Daten der Benutzeroberflächen-Steuerelemente an diese Objekte binden.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Erstellen einer einfachen Datenanwendung mit ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [Neue Verbindungen hinzufügen](../data-tools/add-new-connections.md)

- [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)

- [Verwenden der Entity Data Model-Tools mit Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [Zusätzliche Ressourcen zur Problembehandlung beim Datenzugriff](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Windows Communication Foundation Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [Erstellen und Verwalten von Anwendungen auf Datenebene und Datenbanken in Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [Zusätzliche Ressourcen zur Problembehandlung beim Datenzugriff](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>Weitere Informationen
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
