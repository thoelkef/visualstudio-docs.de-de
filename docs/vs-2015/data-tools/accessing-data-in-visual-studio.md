---
title: Datenzugriff (Accessing data)
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 065a6ae3901f2426db6556cb19e80f543cb8a78f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846666"
---
# <a name="accessing-data-in-visual-studio"></a>Zugreifen auf Daten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie Anwendungen erstellen, die eine Verbindung mit Daten in praktisch allen Datenbankprodukten oder-Diensten in beliebiger Form herstellen – auf einem lokalen Computer, in einem lokalen Netzwerk oder in einem öffentlichen, privaten oder Hybrid Cloud.

 Für Anwendungen in JavaScript, Python, PHP, Ruby oder C++können Sie eine Verbindung mit Daten herstellen, wie Sie nichts anderes tun, indem Sie Bibliotheken abrufen und Code schreiben. Für .NET-Anwendungen stellt Visual Studio Tools bereit, die Sie zum Durchsuchen von Datenquellen, zum Erstellen von Objekt Modellen zum Speichern und Bearbeiten von Daten im Arbeitsspeicher und zum Binden von Daten an die Benutzeroberfläche verwenden können.     Microsoft Azure bietet sdjs für .net, Java, Node. js, PHP, Python, Ruby und Mobile Apps sowie Tools in Visual Studio zum Herstellen einer Verbindung mit Azure Storage.

 Die folgenden Listen enthalten nur einige der vielen Daten Bank-und Speichersysteme, die in Visual Studio verwendet werden können. Die [Microsoft Azure](https://azure.microsoft.com/) Angebote sind Datendienste, die die gesamte Bereitstellung und Verwaltung des zugrunde liegenden Datenspeicher beinhalten.  [Azure Tools für Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) ist eine optionale Komponente, die es Ihnen ermöglicht, direkt von Visual Studio aus mit Azure-Daten speichern zu arbeiten. Die meisten anderen in diesem Abschnitt aufgeführten SQL-und nosql-Daten Bankprodukte können auf einem lokalen Computer, in einem lokalen Netzwerk oder in Microsoft Azure auf einem virtuellen Computer gehostet werden. In diesem Szenario sind Sie für die Verwaltung der Datenbank selbst verantwortlich.

 **Microsoft Azure**

||||
|-|-|-|
|SQL-Datenbank|DocumentDB|Speicher (BLOB, Tabellen, Warteschlangen, Dateien)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

 Und mehr...

 **SQL**

||||
|-|-|-|
|SQL Server 2005 – 2016, einschließlich Express und localdb|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

 Und mehr...

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NDatenbank|OrientDB|RavenDB|
|VelocityDB|||

 Und mehr...

 Viele Datenbankanbieter und Drittanbieter unterstützen die Visual Studio-Integration von nuget-Paketen. Sie können die Angebote auf nuget.org oder über den nuget-Paket-Manager in Visual Studio **(Extras** > **nuget-Paket-Manager** > **Verwalten von nuget-Paketen für die Lösung**) erkunden. Andere Daten Bankprodukte werden in Visual Studio als Erweiterung integriert.   Sie können diese Angebote in der Visual Studio Gallery durchsuchen, indem Sie zu **Tools** > **Erweiterungen und Updates** navigieren und dann im linken Bereich des Dialog Felds **Online** auswählen.  Weitere Informationen finden Sie unter [Installieren von Datenbanksystemen, Tools und Beispielen](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Der erweiterte Support für SQL Server 2005 wurde am 12. April 2016 eingestellt.   Es gibt keine Garantie dafür, dass Data Tools in Visual Studio 2015 und höher nach diesem Datum weiterhin mit SQL Server 2005 funktionieren. Weitere Informationen finden Sie in der [Ankündigung zum Ende des Supports für SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>.NET-Sprachen
 Alle .NET-Daten Zugriffe, einschließlich in .net Core, basieren auf ADO.net, einer Reihe von Klassen, die eine Schnittstelle für den Zugriff auf eine beliebige Art von Datenquelle definieren, sowohl relationale als auch nicht relationale. Visual Studio verfügt über mehrere Tools und Designer, die mit ADO.NET verwendet werden können, um eine Verbindung mit Datenbanken herzustellen, die Daten zu bearbeiten und die Daten dem Benutzer vorzustellen. In der Dokumentation in diesem Abschnitt wird beschrieben, wie diese Tools verwendet werden. Sie können auch direkt mit den ADO.NET-Befehls Objekten programmieren. Weitere Informationen zum direkten Aufrufen der ADO.NET-APIs finden Sie unter [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) in der MSDN Library.

 Informationen zur Datenzugriffs Dokumentation, die sich speziell auf ASP.net bezieht, finden Sie unter [Arbeiten mit Daten](https://docs.microsoft.com/aspnet/web-forms/overview/presenting-and-managing-data/) auf der ASP.NET-Website. Ein Tutorial zur Verwendung von Entity Framework mit ASP.NET MVC finden [Sie unter Getting Started with Entity Framework 6 Code First using MVC 5](https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Universelle Windows-Plattform-Apps (UWP) C# in oder Visual Basic können den Microsoft Azure SDK für .NET verwenden, um auf Azure Storage und andere Azure-Dienste zuzugreifen. Die Windows. Web. HttpClient-Klasse ermöglicht die Kommunikation mit einem beliebigen Rest-Dienst. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem HTTP-Server mithilfe von Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Für die Datenspeicherung auf dem lokalen Computer wird empfohlen, SQLite zu verwenden, das in demselben Prozess wie die app ausgeführt wird. Wenn eine ORM-Ebene (Object-Relational Mapping) erforderlich ist, können Sie Entity Framework verwenden. Weitere Informationen finden Sie unter [Datenzugriff](https://msdn.microsoft.com/windows/uwp/data-access/index) im Windows Developer Center.

 Wenn Sie eine Verbindung mit Azure-Diensten herstellen, stellen Sie sicher, dass Sie die neuesten [Azure SDK-Tools](https://azure.microsoft.com/downloads/)herunterladen.

#### <a name="data-providers"></a>Datenanbieter
 Damit eine Datenbank in ADO.net verwendbar ist, muss Sie über einen benutzerdefinierten *ADO.NET-Datenanbieter* verfügen, oder es muss eine ODBC-oder OLE DB-Schnittstelle verfügbar gemacht werden. Microsoft stellt eine [Liste von ADO.NET-Datenanbietern](https://msdn.microsoft.com/data/dd363565) für SQL Server Produkte sowie ODBC-und OLE DB-Anbieter bereit.

#### <a name="data-modeling"></a>Datenmodellierung
 In .net haben Sie drei Möglichkeiten, um Daten im Arbeitsspeicher zu modellieren und zu bearbeiten, nachdem Sie Sie aus einer Datenquelle abgerufen haben:

 Entity Framework die bevorzugte Microsoft ORM-Technologie. Sie können Sie verwenden, um für relationale Daten als erstklassige .NET-Objekte zu programmieren. Bei neuen Anwendungen sollte es sich um die standardmäßige erste Wahl handeln, wenn ein Modell erforderlich ist. Hierfür ist eine benutzerdefinierte Unterstützung des zugrunde liegenden ADO.NET-Anbieters erforderlich.

 LINQ to SQL einen objektrelationalen Mapper einer früheren Generation. Dies funktioniert gut für weniger komplexe Szenarien, ist jedoch nicht mehr in der aktiven Entwicklung.

 Datasets sind die ältesten der drei Modellierungs Technologien. Es wurde hauptsächlich für die schnelle Entwicklung von "Forms over Data"-Anwendungen entwickelt, bei denen keine großen Datenmengen verarbeitet werden oder komplexe Abfragen oder Transformationen ausgeführt werden. Ein DataSet-Objekt besteht aus Datable-und DataRow-Objekten, die SQL-Datenbankobjekten wesentlich mehr als .NET-Objekte ähneln. Für relativ einfache Anwendungen, die auf SQL-Datenquellen basieren, sind Datasets möglicherweise trotzdem eine gute Wahl.

 Es ist nicht erforderlich, eine dieser Technologien zu verwenden. In einigen Szenarien, insbesondere bei kritischer Leistung, können Sie einfach ein DataReader-Objekt verwenden, um Daten aus der Datenbank zu lesen und die Werte, die Sie benötigen, in ein Auflistungs Objekt, z. b. Listen\<t >, zu kopieren.

### <a name="native-c"></a>Systemeigenes C++
 C++Anwendungen, die eine Verbindung mit SQL Server herstellen, sollten die [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx)verwenden. Sie können auf andere Datenbanken zugreifen, indem Sie [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) oder OLE DB Treiber direkt verwenden. ODBC ist die aktuelle Standarddaten bankschnittstelle, aber die meisten Datenbanksysteme bieten benutzerdefinierte Funktionen, auf die über die ODBC-Schnittstelle nicht zugegriffen werden kann.  OLE DB ist eine veraltete com-Datenzugriffs Technologie, die weiterhin unterstützt wird, aber für neue Anwendungen nicht empfohlen wird.  Weitere Informationen finden Sie unter [Datenzugriff](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 C++Programme, die Rest-Dienste nutzen, können das [ C++ Rest-SDK](https://github.com/Microsoft/cpprestsdk)verwenden.

 C++Programme, die mit Microsoft Azure Storage arbeiten, können den [Microsoft Azure Storage-Client](https://www.nuget.org/packages/wastorage)verwenden.

#### <a name="data-modeling"></a>Datenmodellierung
 Visual Studio stellt keine ORM-Ebene für C++bereit.  [ODB](https://www.codesynthesis.com/products/odb/) ist eine beliebte Open Source-ORM für C++.

 Weitere Informationen zu Legacy Technologien für C++ den visuellen Datenzugriff finden Sie unter [Datenzugriff](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [JavaScript in Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) ist eine erstklassige Sprache zum Entwickeln von plattformübergreifenden apps, UWP-apps, Cloud Services, Websites und Web-Apps. Sie können Bower, Grunt, Gulp, NPM und nuget in Visual Studio verwenden, um Ihre bevorzugten JavaScript-Bibliotheken und-Daten Bankprodukte zu installieren. Stellen Sie eine Verbindung mit Azure Storage und Diensten her, indem Sie sdken von der [Azure-Website](https://azure.microsoft.com/)herunterladen  Edge. js ist eine Bibliothek, die serverseitiges JavaScript (Node. js) mit ADO.NET-Datenquellen verbindet.

### <a name="python"></a>Python
 Installieren Sie [python Tools für Visual Studio](http://microsoft.github.io/PTVS/) zusammen mit Ihrem bevorzugten python-Framework, um CPython-oder IronPython (.net)-Anwendungen zu erstellen.  Die python Tools für Visual Studio-Website enthält mehrere Tutorials zum Verbinden mit Daten, einschließlich [Django und SQL-Datenbank in Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django und MySQL in Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) und [Bottle und MongoDB in Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Installieren von Datenbanksystemen, Tools und Beispielen](../data-tools/installing-database-systems-tools-and-samples.md) Erläutert, wie Sie Daten Bankprodukte und die Visual Studio-Erweiterungen oder-Treiber, die diese unterstützen, abrufen und wie Sie Beispiel Datenbanken für experimentieren und Lernzwecke finden.

 [Visual Studio-Daten Tools für .net](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Beschreibt die Verwendung von Visual Studio Tool Fenstern zum Herstellen einer Verbindung mit Datenquellen, zum Erstellen von Datasets oder Entity Framework Modellen und zum Binden der Daten an Steuerelemente der Benutzeroberfläche.

## <a name="related-topics"></a>Verwandte Themen
 [Daten, Geräte und Analysen](https://msdn.microsoft.com/data-and-devices) Bietet eine Einführung in die Microsoft Intelligent Cloud, einschließlich der Cortana Analytics Suite und der Unterstützung für Internet der Dinge.

 [Microsoft Azure Storage](/azure/storage/) Beschreibt Azure Storage und das Erstellen von Anwendungen mithilfe von Azure-blobdateien,-Tabellen,-Warteschlangen und-Dateien.

 [Azure SQL-Datenbank](https://azure.microsoft.com/documentation/services/sql-database/) Beschreibt das Herstellen einer Verbindung mit Azure SQL-Datenbank, einem relationalen Database as a Service.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Beschreibt die Tools, die das Entwerfen, durchsuchen, testen und Bereitstellen von Daten verbundenen Anwendungen und Datenbanken vereinfachen.

 [ADO.net](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) Beschreibt die ADO.NET-Architektur und die Verwendung der ADO.NET-Klassen zum Verwalten von Anwendungsdaten und interagieren mit Datenquellen und XML.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) Beschreibt, wie Sie Daten Anwendungen erstellen, die es Entwicklern ermöglichen, anstelle einer relationalen Datenbank direkt mit einem konzeptionellen Modell zu programmieren.

 [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Beschreibt, wie [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] verwendet wird, um Datendienste im Internet oder in einem Intranet bereitzustellen, die die [Open Data Protocol (odata)](https://www.odata.org/)implementieren.

 [Daten in Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) -Projektmappen Enthält Links zu Themen, in denen die Funktionsweise von Daten in Office-Lösungen erläutert wird. Dazu gehören Informationen über schemaorientierte Programmierung, Datenzwischenspeicherung und serverseitigen Datenzugriff.

 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Beschreibt die Funktionen, die in C# und Visual Basic integriert sind, und das allgemeine Modell zum Abfragen von relationalen Datenbanken, XML-Dokumenten, Datasets und in-Memory-Auflistungen.

 [XML-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) Erläutert das Arbeiten mit XML-Daten, das Debuggen von XSLT, .NET Framework XML-Funktionen und die Architektur von XML Query.

 [XML-Dokumente und-Daten](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) Bietet eine Übersicht zu einem umfassenden und integrierten Satz von Klassen, die mit XML-Dokumenten und-Daten in der .NET Framework arbeiten.
