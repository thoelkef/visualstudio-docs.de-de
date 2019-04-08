---
title: Zugreifen auf Daten
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
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 5165cf21328b8af1cda63384a5dafbc8dfc2d849
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001707"
---
# <a name="accessing-data-in-visual-studio"></a>Zugreifen auf Daten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


In Visual Studio können Sie Anwendungen, die eine zu Daten in praktisch jedem Datenbankprodukt oder Dienst, der als jedes Formats Verbindung erstellen – auf einem lokalen Computer, auf einem lokalen Netzwerk oder in eine öffentliche, Private oder hybride Cloud.

 Für Anwendungen in JavaScript, Python, PHP, Ruby oder C++ verbinden Sie mit Daten, wie Sie nichts anderes, durch Abrufen von Bibliotheken und Schreiben von Code. Für .NET-Anwendungen bietet Visual Studio Tools, die Sie zum Untersuchen von Datenquellen, erstellen Sie Objektmodelle zu speichern und Bearbeiten von Daten im Arbeitsspeicher und Binden von Daten an die Benutzeroberfläche verwenden können.     Microsoft Azure bietet SDKs für .NET, Java, Node.js, PHP, Python, Ruby und mobilen apps, und in Visual Studio-Tools für die Verbindung mit Azure Storage.

 Die folgenden sind Listen nur einige der vielen Datenbank- und Systeme, die verwendet werden können in Visual Studio. Die [Microsoft Azure](https://azure.microsoft.com/) Angebote sind Datendienste, die alle Bereitstellung und Verwaltung von zugrunde liegenden Datenspeicher enthalten.  [Azure-Tools für Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) ist eine optionale Komponente, die Sie mit der Azure-Datenspeichern direkt aus Visual Studio arbeiten kann. Die meisten anderen SQL- und NoSQL-Datenbankprodukte, die hier aufgeführt sind, können auf einem lokalen Computer in einem lokalen Netzwerk oder in Microsoft Azure auf einem virtuellen Computer gehostet werden. In diesem Szenario können Sie für die Verwaltung der Datenbank selbst verantwortlich.

 **Microsoft Azure**

||||
|-|-|-|
|SQL-Datenbank|DocumentDB|Speicher (Blobs, Tabellen, Warteschlangen, Dateien)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

 Und mehr...

 **SQL**

||||
|-|-|-|
|SQL Server 2005 – 2016, einschließlich Express und LocalDB|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

 Und mehr...

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NDatabase|OrientDB|RavenDB|
|VelocityDB|||

 Und mehr...

 Viele Datenbankhersteller und Drittanbieter Unterstützung von Visual Studio-Integration von NuGet-Pakete. Die Angebote stehen auf nuget.org oder über den NuGet Package Manager in Visual Studio (**Tools** > **NuGet Package Manager** > **Verwalten von NuGet Pakete für Projektmappe**). Andere Datenbankprodukte, in Visual Studio als Erweiterung integrieren.   Sie können diese Angebote im Visual Studio Gallery durchsuchen, indem Sie navigieren zu **Tools** > **Erweiterungen und Updates** auswählen und dann **Online** in der linken Seite der Bereich des Dialogfelds.  Weitere Informationen finden Sie unter [Installieren von Datenbanksystemen, Tools und Beispielen](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
>  Der erweiterte Support für SQL Server 2005 endete am 12. April 2016 eingestellt.   Es gibt keine Garantie, in der Data-Tools in Visual Studio 2015 und höher funktioniert mit SQL Server 2005 nach diesem Datum weiterhin. Weitere Informationen finden Sie unter den [Ankündigung der Ablauf des Supports für SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Sprachen für .NET
 Alle .NET Datenzugriff, einschließlich der in .NET Core, basieren auf ADO.NET eine Reihe von Klassen, die eine Schnittstelle für den Zugriff auf jede Art von relationalen und nicht relationalen Datenquelle definiert. Visual Studio verfügt über mehrere Tools und Designern, die mit ADO.NET können Sie die Verbindung mit Datenbanken arbeiten Manipulation der Daten und für dem Benutzer bereitzustellen. Die Dokumentation in diesem Abschnitt wird beschrieben, wie Sie diese Tools verwenden wird. Sie können auch direkt für den Befehl ADO.NET-Objekte programmieren. Weitere Informationen, die ADO.NET-APIs direkt aufrufen können, finden Sie unter [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) in der MSDN Library.

 Datenzugriffs-Dokumentation, die speziell auf ASP.NET beziehen, finden Sie unter [arbeiten mit Daten](http://www.asp.net/web-forms/overview/presenting-and-managing-data) auf der ASP.NET-Website. Ein Tutorial zur Verwendung von Entity Framework mit ASP.NET MVC finden Sie unter [erste Schritte mit Entity Framework 6 Code First anhand von MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Universelle Windows-Plattform (UWP)-apps in C# oder Visual Basic können das Microsoft Azure SDK für .NET verwenden, den Zugriff auf Azure Storage und andere Azure-Dienste. Die Windows.Web.HttpClient-Klasse ermöglicht die Kommunikation mit RESTful-Dienst. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem HTTP-Server mithilfe von Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Die empfohlene Vorgehensweise werden für die datenspeicherung auf dem lokalen Computer SQLite, verwenden Sie die im selben Prozess wie die app ausgeführt wird. Wenn eine objektrelationale (ORM)-Zuordnungsebene erforderlich ist, können Sie Entity Framework. Weitere Informationen finden Sie unter [Datenzugriff](https://msdn.microsoft.com/windows/uwp/data-access/index) im Windows Developer Center.

 Wenn Sie die Azure-Diensten herstellen, werden Sie sicher, dass die neueste Version herunterladen [Azure SDK-Tools](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Datenanbieter
 Für eine Datenbank in ADO.NET genutzt werden, müssen sie eine benutzerdefinierte *ADO.NET-Datenanbieter* oder anderen muss zur Verfügung stellen einer ODBC- oder OLE DB-Schnittstelle. Microsoft bietet eine [Liste von ADO.NET-Datenanbietern,](https://msdn.microsoft.com/data/dd363565) für SQL Server-Produkte als auch für ODBC und OLE DB-Anbieter.

#### <a name="data-modeling"></a>Datenmodellierung
 In .NET haben Sie drei Optionen für die Modellierung und Bearbeiten von Daten im Arbeitsspeicher, nachdem Sie es aus einer Datenquelle abgerufen haben:

 Entitätsframework die bevorzugte Microsoft-ORM-Technologie. Sie können sie das Programmieren mit relationalen Daten als Objekte erster Klasse .NET verwenden. Für neue Anwendungen sollte es die erste Standardauswahl sein, wenn ein Modell erforderlich ist. Unterstützung für benutzerdefinierte aus den zugrunde liegenden ADO.NET-Anbieter muss.

 LINQ to SQL eine objektrelationale Zuordnung der älteren Generation. Es eignet sich gut für weniger komplexe Szenarien ist jedoch nicht mehr in der aktiven Entwicklung.

 Datasets die älteste von den drei Technologien für die Modellierung. Es dient in erster Linie für die schnelle Entwicklung von Anwendungen für "Forms over Data", in dem Sie keine riesige Datenmengen verarbeiten oder Ausführen von komplexen Abfragen oder Transformationen sind. Ein DataSet-Objekt besteht aus DataTable "und" DataRow-Objekten, die logisch SQL-Datenbankobjekte viel mehr .NET Objekte ähneln. Für relativ einfache Anwendungen, die basierend auf SQL-Datenquellen möglicherweise Datasets weiterhin eine gute Wahl.

 Besteht keine Notwendigkeit, eine dieser Technologien zu verwenden. In einigen Szenarien, insbesondere bei der Leistung kritisch ist, wird einfach können Sie ein DataReader-Objekt aus der Datenbank gelesen, und kopieren Sie die Werte, die Sie benötigen, in ein Auflistungsobjekt, z. B. Liste\<T >.

### <a name="native-c"></a>Systemeigenes C++
 C++-Anwendungen, die Verbindung mit SQL Server verwenden, sollten die [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Sie können auf andere Datenbanken zugreifen, mithilfe von [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) oder direkt für OLE DB-Treiber. ODBC ist der aktuelle standard-Datenbank-Schnittstelle, aber die meisten Datenbanksysteme bereitstellen, benutzerdefinierte Funktionen, die nicht über die ODBC-Schnittstelle zugegriffen werden kann.  OLE DB ist eine ältere com-Datenzugriffs-Technologie, die weiterhin unterstützt, aber nicht für neue Anwendungen empfohlen.  Weitere Informationen finden Sie unter [Datenzugriff](http://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 C++-Programme, die REST-Dienste nutzen können. die [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

 C++-Programme, die Arbeit mit Microsoft Azure Storage können die [Microsoft Azure Storage Client](http://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Datenmodellierung
 Visual Studio bietet eine ORM-Ebene nicht für C++.  [ODB](http://www.codesynthesis.com/products/odb/) ist eine beliebte Open-Source-ORM für C++.

 Weitere Informationen zu älteren Visual C++ von datenzugriffstechnologien, finden Sie unter [Datenzugriff](http://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [JavaScript in Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) ist eine erstklassige Sprache zum Erstellen von plattformübergreifenden apps, UWP-apps, Cloud Services, Websites und Web-apps. Sie können die Bower, Grunt, Gulp, Npm und NuGet in Visual Studio verwenden, Ihre bevorzugten JavaScript-Bibliotheken und die Datenbankprodukte installieren. Verbindung mit Azure-Speicher und Dienste durch Herunterladen des SDKs von der [Azure-Website](https://azure.microsoft.com/).  Edge.js ist eine Bibliothek, die serverseitige JavaScript (Node.js) an ADO.NET-Datenquellen stellt eine Verbindung her.

### <a name="python"></a>Python
 Installieren Sie [Python-Tools für Visual Studio](http://microsoft.github.io/PTVS/) zusammen mit Ihrem bevorzugten Python-Webframework zum Erstellen von Anwendungen für CPython und IronPython (.NET).  Die Python-Tools für Visual Studio-Website verfügt über mehrere Tutorials zum Herstellen einer Verbindung mit Daten sowie [Django und SQL-Datenbank in Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django und MySQL in Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) und [Bottle und MongoDB in Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Installieren von Datenbanksystemen, Tools und Beispielen](../data-tools/installing-database-systems-tools-and-samples.md) erläutert, wie zum Abrufen von Datenbankprodukte und die Visual Studio-Erweiterungen oder Treiber, die sie unterstützen und wo finden Sie Beispieldatenbanken für Experimente und Lernzwecken.

 [Visual Studio-Datentools für .NET](http://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) beschreibt, wie Visual Studio-Toolfenster zum Verbinden mit Datenquellen, Datasets oder Entity Framework-Modelle erstellen und Binden der Daten an Steuerelemente der Benutzeroberfläche.

## <a name="related-topics"></a>Verwandte Themen
 [Daten, Geräte und Analysen](https://msdn.microsoft.com/data-and-devices) bietet eine Einführung in die intelligente Cloud von Microsoft, einschließlich Cortana Analytics Suite und Unterstützung für das Internet der Dinge.

 [Microsoft Azure Storage](/azure/storage/) beschreibt Azure Storage und das Erstellen von Anwendungen mit Azure-Blobs, Tabellen, Warteschlangen und Dateien.

 [Azure SQL-Datenbank](https://azure.microsoft.com/documentation/services/sql-database/) beschreibt, wie Sie eine Verbindung mit Azure SQL-Datenbank, eine relationale Datenbank als Dienst.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) beschreibt die Tools, die das Design, durchsuchen, testen und Bereitstellen von Daten verbundenen Anwendungen und Datenbanken zu vereinfachen.

 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) beschreibt die ADO.NET-Architektur und Verwendung der ADO.NET-Klassen zum Verwalten von Anwendungsdaten und interagieren mit Datenquellen und XML.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) wird beschrieben, wie zum Erstellen von Anwendungen, die Entwicklern das Programmieren für ein konzeptionelles Modell statt direkt in einer relationalen Datenbank zu ermöglichen.

 [WCF Data Services 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) beschreibt, wie [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] Datendienste im Internet oder Intranet bereitgestellt, die implementieren die [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

 [Daten in Office-Projektmappen](http://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) enthält Links zu Themen, die allgemeine Funktionsweise von Daten in Office-Projektmappen erläutern. Dazu gehören Informationen über schemaorientierte Programmierung, Datenzwischenspeicherung und serverseitigen Datenzugriff.

 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) wird beschrieben, die in integrierten Abfragefunktionen C# und Visual Basic und das allgemeine Abfragemodell für relationale Datenbanken, XML-Dokumente, Datasets und speicherinterne Auflistungen.

 [XML-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) erläutert dem Arbeiten mit XML-Daten, Debuggen von XSLT, .NET Framework-XML-Funktionen und die Architektur der XML-Abfrage.

 [XML-Dokumente und Daten](http://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) bietet eine Übersicht über eine umfassende und integrierte Gruppe von Klassen, die Arbeit mit XML-Dokumente und Daten in .NET Framework.
