---
title: Installieren von Datenbanksystemen, Tools und Beispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1dea5adb6903c7beaf39c65909296224afa2a44c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510607"
---
# <a name="installing-database-systems-tools-and-samples"></a>Installieren von Datenbanksystemen, Tools und Beispiele
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Installieren von Datenbanksystemen, Tools und Beispielen](https://docs.microsoft.com/visualstudio/data-tools/installing-database-systems-tools-and-samples).  
  
  
Visual Studio umfasst keine Datenbanksysteme außer denen, die intern verwendet. Um eine Anwendung verbundenen Daten in Visual Studio zu entwickeln, Sie in der Regel das Datenbanksystem auf Ihrem lokalen Entwicklungscomputer installieren und die Anwendung und Datenbank in einer produktionsumgebung dann bereitstellen, wenn sie bereit sind. Für das Datenbanksystem von .NET-Anwendungen zugegriffen werden und in Visual Studio Data Tools-Fenster sichtbar ist muss er einen ADO.NET-Anbieter für Daten verfügen. Ein Anbieter muss speziell Entity Framework unterstützen, wenn Sie Datenmodelle in Ihrer .NET-Anwendung verwenden möchten.     Viele Anbieter werden über den NuGet-Paket-Manager oder über Visual Studio-Katalog angeboten.  
  
 Stellen Sie sicher, dass Sie SQL Server Data Tools in Visual Studio installiert haben, für die SQL-Entwicklung. Klicken Sie auf die **Ansicht** Menü. Wenn Sie SQL Server-Objekt-Explorer nicht angezeigt wird, wechseln Sie zur Systemsteuerung, und Ändern von Visual Studio. Wählen Sie das Installationsprogramm **Microsoft SQL Server Data Tools**.  
  
 Wenn Sie Azure Storage-APIs verwenden, installieren Sie die Azure-Speicher-Emulatoren auf dem lokalen Computer während der Entwicklung, um Gebühren zu vermeiden, bis Sie bereit sind, für die Produktion bereitstellen. Weitere Informationen finden Sie unter [Verwenden des Azure-Speicheremulators für Entwicklung und Tests](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/).  
  
 Die folgende Liste enthält einige der gängigeren Datenbanksystemen, die verwendet werden können, in Visual Studio-Projekten. Die Liste ist nicht vollständig. Eine Liste der Drittanbieter, die Daten ADO.NET-Datenanbieter bieten, die enge Integration in Visual Studio-Tools zu ermöglichen, finden Sie unter [ADO.NET-Datenanbietern](https://msdn.microsoft.com/library/dd363565.aspx).  
  
### <a name="microsoft-sql-server"></a>Microsoft SQL Server  
 SQL Server ist die führende Microsoft-Datenbank bietet. SQL Server 2016 bietet bahnbrechende Leistung, erweiterter Sicherheit und funktionsreiche, integrierte berichterstellung und Analysen. Wird in verschiedenen Editionen, die für unterschiedliche Verwendungszwecke ausgelegt sind: hochgradig skalierbare, leistungsstarke Business Analytics, für die Verwendung auf einem einzelnen Computer. SQL Server Express ist eine voll funktionsfähige Edition von SQL Server, die für die weiterverteilung und Einbetten von zugeschnitten sind.  LocalDB ist eine vereinfachte Edition von SQL Server Express, die erfordert keine Konfiguration und in der Anwendung ausgeführt wird. Sie können eine oder beide Produkte über [der SQL Server Express-Download-Seite](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx).    Viele der SQL-Beispiele in diesem Abschnitt verwenden Sie SQL Server LocalDB. SQL Server Management Studio (SSMS) ist eine eigenständige Datenbank-verwaltungsanwendung, die über mehr Funktionen als die in Visual Studio SQL Server Objekt-Explorer bereitgestellten verfügt. Sie können SSMS über den vorherigen Link abrufen.  
  
### <a name="oracle"></a>Oracle  
 Sie können eine kostenpflichtige oder kostenlose Edition der Oracle-Datenbank aus der [Oracle Technologienetzwerk](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) Seite. Entwurfszeitunterstützung für Entity Framework und TableAdapter-Steuerelemente, müssen Sie die [Oracle Developer Tools für Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Andere offizielle Oracle-Produkte, einschließlich von den Oracle Instant Client, stehen über den NuGet-Paket-Manager zur Verfügung.  Sie können Oracle-Beispielschemas herunterladen, indem Sie die Anweisungen in der [Oracle-Onlinedokumentation](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).  
  
### <a name="mysql"></a>MySQL  
 MySQL ist ein beliebter Open-Source-Datenbank, die häufig in Unternehmen und Websites verwendet wird. Downloads für MySQL MySQL für Visual Studio und verwandte Produkte sind [MySQL unter Windows](http://www.mysql.com/why-mysql/windows/).  Drittanbieter bieten verschiedene Visual Studio-Erweiterungen und eigenständigen verwaltungsanwendungen für MySQL. Sie können die Angebote in den NuGet Package Manager Durchsuchen (**Tools** > **NuGet Package Manager** > **NuGet-Pakete für Projektmappe verwalten**) .  
  
### <a name="postgresql"></a>PostgreSQL  
 PostgreSQL ist einem relationalen Datenbanksystem kostenlos, Open-Source-Objekt. Um die Installation auf Windows, Sie können es herunterladen aus dem [PostgreSQL-Downloadseite](http://www.postgresql.org/download/windows/).  Sie können auch PostgreSQL aus dem Quellcode erstellen.  Das PostgreSQL-Core-System enthält eine Schnittstelle der C-Sprache. Viele Drittanbieter stellen NuGet-Pakete für die Verwendung von PostgreSQL aus .NET-Anwendungen bereit.  Sie können die Angebote in den NuGet Package Manager Durchsuchen (**Tools** > **NuGet Package Manager** > **NuGet-Pakete für Projektmappe verwalten**) . Die am häufigsten verwendete Paket vielleicht erfolgt über [npgsql.org](http://www.npgsql.org).  
  
### <a name="sqlite"></a>SQLite  
 SQLite ist eine eingebettete SQL-Datenbank-Engine, die im Prozess der Anwendung ausgeführt wird. Sie können es von der [SQLite-Downloadseite](http://www.sqlite.org/download.html). Viele Drittanbieter-NuGet-Pakete für SQLite sind ebenfalls verfügbar. Sie können die Angebote in den NuGet Package Manager Durchsuchen (**Tools** > **NuGet Package Manager** > **NuGet-Pakete für Projektmappe verwalten**) .  
  
### <a name="firebird"></a>Firebird  
 Firebird ist ein Open-Source-SQL-Datenbank. Sie können es von der [Firebird-Downloadseite](http://firebirdsql.org/en/downloads/). Ein ADO.NET-Datenanbieter steht über den NuGet-Paket-Manager zur Verfügung.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Ermitteln der Version und Edition von SQL Server und dessen Komponenten](http://support.microsoft.com/kb/321185)

