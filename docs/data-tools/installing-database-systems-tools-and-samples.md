---
title: "Visual Studio-Datenbankkompatibilität | Microsoft Docs"
ms.custom: 
ms.date: 09/06/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 2b3a551f19e3410b5f56ebe994676666cdc3d4e1
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="compatible-database-systems-for-visual-studio"></a>Kompatiblen Datenbanksystemen für Visual Studio

Zum Entwickeln einer Anwendung verbundenen Daten in Visual Studio das Datenbanksystem in der Regel auf dem lokalen Entwicklungscomputer installieren und die Anwendung und die Datenbank in einer produktiven Umgebung dann bereitstellen, wenn sie bereit sind. Visual Studio installiert SQL Server Express LocalDB auf dem Computer als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung. Diese LocalDB-Instanz ist nützlich für die Anwendungsentwicklung verbundenen Daten schnell und einfach.

Ein Datenbanksystem von .NET-Anwendungen zugegriffen werden kann und in Fenstern in Visual Studio Data Tools sichtbar sein sollen müssen sie eine ADO.NET-Datenanbieter. Ein Anbieter muss insbesondere Entity Framework unterstützen, wenn Sie Entity Data Models in Ihrer .NET-Anwendung verwenden möchten. Viele Anbieter sind über NuGet-Paket-Manager oder über den Visual Studio Marketplace angeboten.

Bei Verwendung von Azure-Speicher-APIs installieren Sie die Azure-Speicher-Emulatoren auf dem lokalen Computer während der Entwicklung, um Gebühren zu vermeiden, bis Sie zur Bereitstellung bis hin zur Produktion bereit sind. Weitere Informationen finden Sie unter [Verwenden des Azure-Speicheremulators für Entwicklung und Tests](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/).

Die folgende Liste enthält einige der gängigeren Datenbanksystemen, die verwendet werden können, in Visual Studio-Projekten. Die Liste ist nicht vollständig. Eine Liste der Drittanbieter, die Daten ADO.NET-Datenanbieter bieten, die umfassende Integration in Visual Studio-Tools zu ermöglichen, finden Sie unter [ADO.NET-Datenanbietern](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server ist die Microsoft-datenbankflaggschiffs-Datenbank bietet. SQL Server 2016 bietet bahnbrechende Leistung, erweiterter Sicherheit und umfassende und integrierte Berichte und Analysen. Wird in verschiedenen Editionen, die für unterschiedliche Verwendungszwecke entwickelt wurden: aus hochgradig skalierbare, leistungsstarke Business Analytics, auf einem einzelnen Computer verwenden. SQL Server Express ist eine voll ausgestattete-Edition von SQL Server, die für die Verteilung und Einbetten zugeschnitten ist.  LocalDB ist eine vereinfachte Edition von SQL Server Express, die erfordert keine Konfiguration und in Ihrer Anwendung-Prozess ausgeführt wird. Sie können eine oder beide Produkte herunterladen [die Downloadseite für SQL Server Express](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx). Viele SQL-Beispiele in diesem Abschnitt verwenden Sie SQL Server LocalDB. SQL Server Management Studio (SSMS) ist eine eigenständige Datenbank-verwaltungsanwendung, die mehr Funktionalität als neues in Visual Studio SQL Server Objekt-Explorer bereitgestellt wird. Sie können die vorherige Verknüpfung SSMS bekommen.

## <a name="oracle"></a>Oracle

Sie können eine kostenpflichtige oder kostenlose Edition von der Oracle-Datenbank aus der [Oracle Technologienetzwerk](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) Seite. Zur Entwurfszeit Unterstützung für Entity Framework und TableAdaptern, müssen Sie die [Oracle Developer Tools für Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Andere offizielle Oracle-Produkte, einschließlich der Oracle Instant Client sind über NuGet-Paket-Manager verfügbar.  Sie können die Oracle-Beispielschemas herunterladen, anhand der Anweisungen in der [Oracle-Onlinedokumentation](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL ist ein beliebter Open Source-Datenbank, die häufig in Unternehmen und Websites verwendet wird. Downloads für MySQL, MySQL für Visual Studio und verwandte Produkte finden Sie am [MySQL für Windows](http://www.mysql.com/why-mysql/windows/).  Drittanbieter bieten verschiedene Visual Studio-Erweiterungen und eigenständigen verwaltungsanwendungen für MySQL. Sie können die Angebote im NuGet-Paket-Manager Durchsuchen (**Tools** > **NuGet Package Manager** > **NuGet-Pakete für Projektmappe verwalten**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL ist einem relationalen Datenbanksystem kostenlos, Open Source-Objekt. Um die Installation unter Windows, Sie können es herunterladen aus der [PostgreSQL-Downloadseite](http://www.postgresql.org/download/windows/).  Sie können auch PostgreSQL aus dem Quellcode erstellen.  PostgreSQL-Core-System enthält eine C-Sprache-Schnittstelle. Viele Drittanbieter bieten NuGet-Pakete für die Verwendung von PostgreSQL von .NET-Anwendungen.  Sie können die Angebote im NuGet-Paket-Manager Durchsuchen (**Tools** > **NuGet Package Manager** > **NuGet-Pakete für Projektmappe verwalten**) . Vielleicht die am häufigsten verwendeten-skriptpakets von [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite ist ein embedded SQL-Datenbankmodul, die in den Prozess der Anwendung ausgeführt wird. Sie können hier herunterladen: aus der [SQLite-Downloadseite](http://www.sqlite.org/download.html). Viele Drittanbieter-NuGet-Pakete für SQLite sind auch verfügbar. Sie können die Angebote im NuGet-Paket-Manager Durchsuchen (**Tools** > **NuGet Package Manager** > **NuGet-Pakete für Projektmappe verwalten**) .

## <a name="firebird"></a>Firebird

Firebird ist ein Open Source-SQL-Datenbank. Sie können hier herunterladen: aus der [Firebird Downloadseite](http://firebirdsql.org/en/downloads/). Ein Datenanbieter von ADO.NET ist über NuGet-Paket-Manager verfügbar.

## <a name="see-also"></a>Siehe auch

[Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
[Gewusst wie: Ermitteln der Version und Edition von SQL Server und seinen Komponenten](http://support.microsoft.com/kb/321185)