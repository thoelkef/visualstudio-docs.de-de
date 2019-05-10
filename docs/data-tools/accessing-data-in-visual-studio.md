---
title: Datenzugriff und -tools
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 16cbdb0a673f503dcee49b7a323d1453ee93532a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818227"
---
# <a name="access-data-in-visual-studio"></a>Zugreifen auf Daten in Visual Studio

In Visual Studio können Sie Anwendungen, die eine zu Daten in praktisch jedem Datenbankprodukt oder Dienst, der als jedes Formats Verbindung erstellen – auf einem lokalen Computer, auf einem lokalen Netzwerk oder in eine öffentliche, Private oder hybride Cloud.

Für Anwendungen in JavaScript, Python, PHP, Ruby oder C++ verbinden Sie mit Daten, wie Sie nichts anderes, durch Abrufen von Bibliotheken und Schreiben von Code. Für .NET-Anwendungen bietet Visual Studio Tools, die Sie zum Untersuchen von Datenquellen, erstellen Sie Objektmodelle zu speichern und Bearbeiten von Daten im Arbeitsspeicher und Binden von Daten an die Benutzeroberfläche verwenden können. Microsoft Azure bietet SDKs für .NET, Java, Node.js, PHP, Python, Ruby und mobilen apps, und in Visual Studio-Tools für die Verbindung mit Azure Storage.

Die folgenden sind Listen nur einige der vielen Datenbank- und Systeme, die verwendet werden können in Visual Studio. Die [Microsoft Azure](https://azure.microsoft.com/) Angebote sind Datendienste, die alle Bereitstellung und Verwaltung von zugrunde liegenden Datenspeicher enthalten. Die **Azure-Entwicklung** arbeitsauslastung in [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) können Sie mit der Azure-Datenspeichern direkt aus Visual Studio arbeiten.

![Workload „Azure-Entwicklung“](media/azure-development-workload.png)

Die meisten anderen SQL- und NoSQL-Datenbankprodukte, die hier aufgeführt sind, können auf einem lokalen Computer in einem lokalen Netzwerk oder in Microsoft Azure auf einem virtuellen Computer gehostet werden. Wenn Sie die Datenbank auf einem virtuellen Microsoft Azure-Computer hosten, sind Sie verantwortlich für die Verwaltung der Datenbank selbst.

**Microsoft Azure**

- SQL-Datenbank
- Azure Cosmos DB
- Speicher (Blobs, Tabellen, Warteschlangen, Dateien)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- Und mehr...

**SQL**

- SQL Server 2005-2016 (einschließlich Express und LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- Und mehr...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB|
- RavenDB
- VelocityDB
- Und mehr...

::: moniker range="vs-2017"

Viele Datenbankhersteller und Drittanbieter Unterstützung von Visual Studio-Integration von NuGet-Pakete. Die Angebote stehen auf nuget.org oder über den NuGet Package Manager in Visual Studio (**Tools** > **NuGet Package Manager** > **Verwalten von NuGet Pakete für Projektmappe**). Andere Datenbankprodukte, in Visual Studio als Erweiterung integrieren. Sie können diese Angebote im Durchsuchen der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) navigieren **Tools** > **Erweiterungen und Updates** auswählen und dann  **Online** im linken Bereich des Dialogfelds. Weitere Informationen finden Sie unter [kompatible Datenbanksysteme für Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Viele Datenbankhersteller und Drittanbieter Unterstützung von Visual Studio-Integration von NuGet-Pakete. Die Angebote stehen auf nuget.org oder über den NuGet Package Manager in Visual Studio (**Tools** > **NuGet Package Manager** > **Verwalten von NuGet Pakete für Projektmappe**). Andere Datenbankprodukte, in Visual Studio als Erweiterung integrieren. Sie können diese Angebote im Durchsuchen der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) navigieren **Erweiterungen** > **Verwalten von Erweiterungen** auswählen und dann  **Online** im linken Bereich des Dialogfelds. Weitere Informationen finden Sie unter [kompatible Datenbanksysteme für Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> Der erweiterte Support für SQL Server 2005 endete am 12. April 2016 eingestellt. Es gibt keine Garantie dafür, die Data-Tools in Visual Studio 2015 und höher arbeiten mit SQL Server 2005 weiterhin vorhanden. Weitere Informationen finden Sie unter den [Ankündigung der Ablauf des Supports für SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Sprachen für .NET

Alle .NET Datenzugriff, einschließlich der in .NET Core, basieren auf ADO.NET eine Reihe von Klassen, die eine Schnittstelle für den Zugriff auf jede Art von relationalen und nicht relationalen Datenquelle definiert. Visual Studio verfügt über mehrere Tools und Designern, die mit ADO.NET können Sie die Verbindung mit Datenbanken arbeiten Manipulation der Daten und für dem Benutzer bereitzustellen. Die Dokumentation in diesem Abschnitt wird beschrieben, wie Sie diese Tools verwenden wird. Sie können auch direkt für den Befehl ADO.NET-Objekte programmieren. Weitere Informationen, die ADO.NET-APIs direkt aufrufen können, finden Sie unter [ADO.NET](/dotnet/framework/data/adonet/index).

Datenzugriffs-Dokumentation im Zusammenhang mit ASP.NET finden Sie [arbeiten mit Daten](https://www.asp.net/web-forms/overview/presenting-and-managing-data) auf der ASP.NET-Website. Ein Tutorial zur Verwendung von Entity Framework mit ASP.NET MVC finden Sie unter [erste Schritte mit Entity Framework 6 Code First anhand von MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Universelle Windows-Plattform (UWP)-apps in c# oder Visual Basic können das Microsoft Azure SDK für .NET verwenden, den Zugriff auf Azure Storage und andere Azure-Dienste. Die Windows.Web.HttpClient-Klasse ermöglicht die Kommunikation mit RESTful-Dienst. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem HTTP-Server mithilfe von Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Die empfohlene Vorgehensweise werden für die datenspeicherung auf dem lokalen Computer SQLite, verwenden Sie die im selben Prozess wie die app ausgeführt wird. Wenn eine objektrelationale (ORM)-Zuordnungsebene erforderlich ist, können Sie Entity Framework. Weitere Informationen finden Sie unter [Datenzugriff](/windows/uwp/data-access/index) im Windows Developer Center.

Wenn Sie die Azure-Diensten herstellen, werden Sie sicher, dass die neueste Version herunterladen [Azure SDK-Tools](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Datenanbieter

Für eine Datenbank in ADO.NET genutzt werden, müssen sie eine benutzerdefinierte *ADO.NET-Datenanbieter* oder anderen muss zur Verfügung stellen einer ODBC- oder OLE DB-Schnittstelle. Microsoft bietet eine [Liste von ADO.NET-Datenanbietern,](https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) für SQL Server-Produkte sowie ODBC- und OLE DB-Anbieter.

### <a name="data-modeling"></a>Datenmodellierung

In .NET haben Sie drei Optionen für die Modellierung und Bearbeiten von Daten im Arbeitsspeicher, nachdem Sie es aus einer Datenquelle abgerufen haben:

[Entitätsframework](../data-tools/entity-data-model-tools-in-visual-studio.md) die bevorzugte Microsoft-ORM-Technologie. Sie können sie das Programmieren mit relationalen Daten als Objekte erster Klasse .NET verwenden. Für neue Anwendungen sollte es die erste Standardauswahl sein, wenn ein Modell erforderlich ist. Unterstützung für benutzerdefinierte aus den zugrunde liegenden ADO.NET-Anbieter muss.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) eine objektrelationale Zuordnung der älteren Generation. Es eignet sich gut für weniger komplexe Szenarien ist jedoch nicht mehr in der aktiven Entwicklung.

[Datasets](../data-tools/dataset-tools-in-visual-studio.md) die älteste von den drei Technologien für die Modellierung. Es dient in erster Linie für die schnelle Entwicklung von Anwendungen für "Forms over Data", in dem Sie keine riesige Datenmengen verarbeiten oder Ausführen von komplexen Abfragen oder Transformationen sind. Ein DataSet-Objekt besteht aus DataTable "und" DataRow-Objekten, die logisch SQL-Datenbankobjekte viel mehr .NET Objekte ähneln. Für relativ einfache Anwendungen, die basierend auf SQL-Datenquellen möglicherweise Datasets weiterhin eine gute Wahl.

Besteht keine Notwendigkeit, eine dieser Technologien zu verwenden. In einigen Szenarien, insbesondere bei der Leistung kritisch ist, wird einfach können Sie ein DataReader-Objekt aus der Datenbank gelesen, und kopieren Sie die Werte, die Sie benötigen, in ein Auflistungsobjekt, z. B. Liste\<T >.

## <a name="native-c"></a>Systemeigenes C++

C++-Anwendungen, die Verbindung mit SQL Server verwenden, sollten die [Microsoft® ODBC Driver 13.1 für SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) in den meisten Fällen. Wenn der Server verknüpft sind, dann OLE DB erforderlich ist und für, die Sie verwenden die [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Sie können auf andere Datenbanken zugreifen, mithilfe von [ODBC](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) oder direkt für OLE DB-Treiber. ODBC ist der aktuelle standard-Datenbank-Schnittstelle, aber die meisten Datenbanksysteme bereitstellen, benutzerdefinierte Funktionen, die nicht über die ODBC-Schnittstelle zugegriffen werden kann. OLE DB ist eine ältere com-Datenzugriffs-Technologie, die weiterhin unterstützt, aber nicht für neue Anwendungen empfohlen. Weitere Informationen finden Sie unter [-Datenzugriff in Visual C++](/cpp/data/data-access-in-cpp).

C++-Programme, die REST-Dienste nutzen können. die [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

C++-Programme, die Arbeit mit Microsoft Azure Storage können die [Microsoft Azure Storage Client](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Die datenmodellierung&mdash;Visual Studio bietet keine ORM-Ebene für C++. [ODB](https://www.codesynthesis.com/products/odb/) ist eine beliebte Open-Source-ORM für C++.

Weitere Informationen zum Verbinden mit Datenbanken von C++-apps finden Sie unter [Visual Studio-Datentools für C++](../data-tools/visual-studio-data-tools-for-cpp.md). Weitere Informationen zu älteren Visual C++ von datenzugriffstechnologien, finden Sie unter [Datenzugriff](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript in Visual Studio](/scripting/javascript/javascript-language-reference) ist eine erstklassige Sprache zum Erstellen von plattformübergreifenden apps, UWP-apps, Cloud Services, Websites und Web-apps. Sie können die Bower, Grunt, Gulp, Npm und NuGet in Visual Studio verwenden, Ihre bevorzugten JavaScript-Bibliotheken und die Datenbankprodukte installieren. Verbindung mit Azure-Speicher und Dienste durch Herunterladen des SDKs von der [Azure-Website](https://azure.microsoft.com/). Edge.js ist eine Bibliothek, die serverseitige JavaScript (Node.js) an ADO.NET-Datenquellen stellt eine Verbindung her.

## <a name="python"></a>Python

Installieren Sie [Python-Unterstützung in Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) Python-Anwendungen zu erstellen. Die Dokumentation zu Azure verfügt über mehrere Tutorials zum Herstellen einer Verbindung mit Daten sowie die folgenden:

- [Django und SQL­Datenbank in Azure](/azure/app-service/app-service-web-get-started-python)
- [Django und MySQL in Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Arbeiten mit [Blobs](/azure/storage/blobs/storage-quickstart-blobs-python), [Dateien](/azure/storage/files/storage-python-how-to-use-file-storage), [Warteschlangen](/azure/storage/queues/storage-python-how-to-use-queue-storage), und [Tabellen (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Verwandte Themen

[Microsoft-AI-Plattform](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;bietet eine Einführung in die intelligente Cloud von Microsoft, einschließlich Cortana Analytics Suite und Unterstützung für das Internet der Dinge.

[Microsoft Azure Storage](/azure/storage/)&mdash;beschreibt Azure Storage und das Erstellen von Anwendungen mit Azure-Blobs, Tabellen, Warteschlangen und Dateien.

[Azure SQL-Datenbank](/azure/sql-database/)&mdash;beschreibt, wie Sie eine Verbindung mit Azure SQL-Datenbank, eine relationale Datenbank als Dienst.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;beschreibt die Tools, die das Design, durchsuchen, testen und Bereitstellen von Daten verbundenen Anwendungen und Datenbanken zu vereinfachen.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;Beschreibt die ADO.NET-Architektur und die Verwendung der ADO.NET-Klassen zum Verwalten von Anwendungsdaten und Interagieren mit Datenquellen und XML.

[ADO.NET Entity Framework](https://docs.microsoft.com/ef/ef6/)&mdash;wird beschrieben, wie zum Erstellen von Anwendungen, die Entwicklern das Programmieren für ein konzeptionelles Modell statt direkt in einer relationalen Datenbank zu ermöglichen.

[WCF Data Services 4.5](/dotnet/framework/data/wcf/index)&mdash;beschreibt, wie [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] Datendienste im Internet oder Intranet bereitgestellt, die implementieren die [Open Data Protocol (OData)](https://www.odata.org/).

[Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)&mdash;enthält Links zu Themen, die allgemeine Funktionsweise von Daten in Office-Projektmappen erläutern. Dazu gehören Informationen über schemaorientierte Programmierung, Datenzwischenspeicherung und serverseitigen Datenzugriff.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;wird beschrieben, die Abfragefunktionen, die in c# und Visual Basic sowie das allgemeine Abfragemodell für relationale Datenbanken, XML-Dokumente, Datasets und speicherinterne Auflistungen integriert.

[XML-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;erläutert dem Arbeiten mit XML-Daten, Debuggen von XSLT, .NET Framework-XML-Funktionen und die Architektur der XML-Abfrage.

[XML-Dokumente und Daten](/dotnet/standard/data/xml/index)&mdash;bietet eine Übersicht über eine umfassende und integrierte Gruppe von Klassen, die Arbeit mit XML-Dokumente und Daten in .NET Framework.
