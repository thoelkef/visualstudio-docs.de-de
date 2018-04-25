---
title: Zugreifen auf Daten in Visual Studio
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
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a7c7e031eb3fbe0330ab752882c8ac89eb7617bf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="accessing-data-in-visual-studio"></a>Zugreifen auf Daten in Visual Studio

In Visual Studio, erstellen Sie Anwendungen, die eine zu Daten in praktisch jeder Datenbankprodukts oder Diensts, in einem beliebigen Format überall Verbindung – auf einem lokalen Computer, auf ein lokales Netzwerk oder in einer öffentlichen, privaten oder Hybrid-Cloud.

Für Anwendungen in JavaScript, Python, PHP, Ruby oder C++ verbinden Sie mit Daten, wie Sie etwas anderes, durch Abrufen von Bibliotheken und Schreiben von Code. Für .NET-Anwendungen bietet Visual Studio Tools, die Sie zum Durchsuchen der Datenquellen, erstellen Sie Objektmodelle zum Speichern und Bearbeiten von Daten im Arbeitsspeicher und Binden von Daten an die Benutzeroberfläche verwenden können. Microsoft Azure bietet SDKs für .NET, Java, Node.js, PHP, Python, Ruby, und mobile apps und in Visual Studio-Tools für die Verbindung mit Azure-Speicher.

Die folgenden Listen anzeigen nur einige der vielen Datenbank- und Systeme, die verwendet werden können, aus Visual Studio. Die [Microsoft Azure](https://azure.microsoft.com/) Angebote sind Datendienste, die alle Bereitstellung und Verwaltung von den zugrunde liegenden Datenspeicher enthalten.  [Azure Tools für Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) ist eine optionale Komponente, die Ihnen ermöglicht, mit der Azure-Datenspeichern direkt in Visual Studio arbeiten. Die meisten anderen SQL- und NoSQL-Datenbankprodukte, die hier aufgeführt sind, können auf einem lokalen Computer in einem lokalen Netzwerk oder in Microsoft Azure auf einem virtuellen Computer gehostet werden. In diesem Szenario sind Sie verantwortlich für die Verwaltung der Datenbank selbst.

**Microsoft Azure**

||||
|-|-|-|
|SQL-Datenbank|Azure-Cosmos-DB|Speicher (Blobs, Tabellen, Warteschlangen, -Dateien)|
|SQL Datawarehouse|SQL Server Stretch-Datenbank|StorSimple|

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

Viele Datenbankhersteller und Drittanbieter unterstützen die Integration von Visual Studio NuGet-Pakete. Sie können die Angebote nuget.org oder über die NuGet-Paket-Manager in Visual Studio Durchsuchen (**Tools** > **NuGet Package Manager** > **Verwalten von NuGet Pakete für Projektmappe**). Andere Datenbankprodukte werden als eine Erweiterung in Visual Studio integrieren. Sie können diese Angebote in Visual Studio Marketplace durchsuchen, navigieren Sie zur **Tools**, **Erweiterungen und Updates** auswählen und dann **Online** im linken Bereich von der Das Dialogfeld. Weitere Informationen finden Sie unter [kompatiblen Datenbanksystemen für Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Der erweiterte Support für SQL Server 2005 endete am 12. April 2016 eingestellt. Es gibt keine Garantie, die Data Tools in Visual Studio 2015 und höher mit SQL Server 2005 nach diesem Datum können auch weiterhin. Weitere Informationen finden Sie unter der [Ankündigung von End-of-Support für SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>.NET Sprachen

Alle .NET-Datenzugriff in .NET Core, einschließlich basiert auf ADO.NET eine Reihe von Klassen, die eine Schnittstelle für den Zugriff auf eine beliebige Art von relationalen und nicht relationalen Datenquelle definiert. Visual Studio verfügt über mehrere Tools und Designern, die mit ADO.NET können Sie die Verbindung mit Datenbanken arbeiten, die Daten bearbeitet und präsentieren der Daten für dem Benutzer. Die Dokumentation in diesem Abschnitt wird beschrieben, wie Sie diese Tools verwenden wird. Sie können auch direkt die Befehlsobjekte ADO.NET programmieren. Weitere Informationen zu ADO.NET-APIs direkt aufrufen, finden Sie unter [ADO.NET](/dotnet/framework/data/adonet/index).

Insbesondere im Zusammenhang mit ASP.NET Datenzugriffs-Dokumentation finden Sie [arbeiten mit Daten](http://www.asp.net/web-forms/overview/presenting-and-managing-data) auf der ASP.NET-Website. Ein Lernprogramm zur Verwendung von Entity Framework mit ASP.NET MVC, finden Sie unter [erste Schritte mit Entity Framework 6 Code First mit MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Universelle Windows-Plattform (UWP)-apps in c# oder Visual Basic können das Microsoft Azure SDK für .NET verwenden, den Zugriff auf Azure-Speicher und anderen Azure-Diensten. Die Klasse Windows.Web.HttpClient ermöglicht die Kommunikation mit RESTful-Dienst. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem HTTP-Server über Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Die empfohlene Vorgehensweise werden für die datenspeicherung auf dem lokalen Computer SQLite, verwenden Sie die in demselben Prozess wie die app ausgeführt wird. Wenn eine Ebene ORM (Objektrelationales Mapping) erforderlich ist, können Sie die Entity Framework. Weitere Informationen finden Sie unter [Datenzugriff](/windows/uwp/data-access/index) im Windows Developer Center.

Wenn Sie eine Verbindung zu Azure-Diensten herstellen, achten Sie darauf, die neueste [Azure SDK-Tools](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Datenanbieter

Für eine Datenbank in ADO.NET verwendet werden, müssen sie eine benutzerdefinierte *ADO.NET-Datenanbieter* oder anderen verfügbar machen eine ODBC- oder OLE DB-Schnittstelle. Microsoft bietet eine [Liste von ADO.NET-Datenanbietern,](https://msdn.microsoft.com/data/dd363565) für SQL Server-Produkte als auch ODBC- und OLE DB-Anbieter.

### <a name="data-modeling"></a>Die datenmodellierung

In .NET haben Sie drei Möglichkeiten für das modellieren und Bearbeiten von Daten im Arbeitsspeicher, nachdem Sie sie aus einer Datenquelle abgerufen wurden:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Microsoft ORM bevorzugt. Sie können es zum Programmieren mit relationalen Daten als erstrangige .NET-Objekte verwenden. Neue Anwendungen sollte die erste Standardauswahl sein, wenn ein Modell erforderlich ist. Es muss vom zugrunde liegenden ADO.NET-Anbieter benutzerdefinierte unterstützt werden.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) eine objektrelationale frühere Generation-Mapper. Es eignet sich gut für weniger komplexe Szenarien ist jedoch nicht mehr in der aktiven Entwicklung.

[Datasets](../data-tools/dataset-tools-in-visual-studio.md) die älteste der drei-modellierungstechnologien. Es dient in erster Linie für die schnelle Entwicklung von Anwendungen "Formulare über Daten", in dem Sie nicht verarbeiten große Datenmengen oder komplexen Abfragen oder Transformationen ausgeführt werden. Ein DataSet-Objekt besteht aus DataTable und DataRow-Objekte, die SQL-Objekte logisch viel mehr als .NET Objekte ähneln. Relativ einfache Anwendungen, die auf SQL-Datenquellen basieren möglicherweise Datasets weiterhin eine gute Wahl.

Es ist nicht erforderlich, eine dieser Technologien zu verwenden. In einigen Szenarien, insbesondere bei der Leistung kritisch ist, wird einfach können Sie ein DataReader-Objekt aus der Datenbank gelesen, und kopieren die Werte, die Sie benötigen, in ein Auflistungsobjekt, z. B. Liste\<T >.

## <a name="native-c"></a>Systemeigenes C++

C++-Anwendungen, die Verbindung mit SQL Server verwenden, sollten die [Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) in den meisten Fällen. Wenn die Server verknüpft sind, OLE DB-erforderlich ist und für die Sie verwenden die [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Sie können auf andere Datenbanken zugreifen, mithilfe von [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) oder direkt die OLE DB-Treiber. ODBC ist die aktuelle standard-Datenbank-Schnittstelle, aber die meisten Datenbanksysteme bereitstellen, benutzerdefinierte Funktionen, die über die ODBC-Schnittstelle nicht zugegriffen werden kann. OLE DB ist eine veraltete com-Datenzugriffs-Technologie, die weiterhin unterstützt wird, aber nicht für neue Anwendungen empfohlen. Weitere Informationen finden Sie unter [-Datenzugriff in Visual C++](/cpp/data/data-access-in-cpp).

C++-Programmen, die REST-Dienste nutzen können die [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

C++-Programmen, die mit Microsoft Azure-Speicher funktionieren können die [Microsoft Azure Storage Client](http://www.nuget.org/packages/wastorage).

Die datenmodellierung&mdash;Visual Studio bietet keine ORM-Ebene für C++. [ODB](http://www.codesynthesis.com/products/odb/) ist eine beliebte Open Source-ORM für C++.

Weitere Informationen zum Verbinden mit Datenbanken von C++-apps finden Sie unter [Daten Visual Studio-Tools für C++](../data-tools/visual-studio-data-tools-for-cpp.md). Weitere Informationen zu älteren Visual C++-Datenzugriffs-Technologien finden Sie unter [Datenzugriff](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[In Visual Studio JavaScript](/scripting/javascript/javascript-language-reference) ist eine der hauptprogrammiersprachen zum Erstellen von plattformübergreifenden apps, uwp-apps, Cloud-Dienste, Websites und Web-apps. Bower, Grunt, Gulp, Npm und von NuGet in Visual Studio können um Ihre bevorzugten JavaScript-Bibliotheken und Produkte zu installieren. Verbinden mit Azure-Speicher und Diensten durch Herunterladen des SDKs aus der [Azure-Website](https://azure.microsoft.com/). Edge.js ist eine Bibliothek, die serverseitige JavaScript (Node.js) mit ADO.NET-Datenquellen verbunden.

## <a name="python"></a>Python

Installieren Sie [Python-Unterstützung in Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) Python-Anwendungen zu erstellen. Die Azure-Dokumentation enthält mehrere Lernprogramme zum Herstellen einer Verbindung mit Daten, einschließlich der folgenden:

- [Django und SQL­Datenbank in Azure](/azure/app-service/app-service-web-get-started-python)
- [Django und MySQL auf Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Arbeiten mit [Blobs](/azure/storage/blobs/storage-quickstart-blobs-python), [Dateien](/azure/storage/files/storage-python-how-to-use-file-storage), [Warteschlangen](/azure/storage/queues/storage-python-how-to-use-queue-storage), und [Tabellen (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Verwandte Themen

[Microsoft AI-Plattform](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;bietet eine Einführung in die intelligente Cloud von Microsoft, einschließlich Cortana Analytics Suite und Unterstützung für Internet der Dinge.

[Microsoft Azure Storage](/azure/storage/)&mdash;beschreibt Azure-Speicher, und Erstellen von Anwendungen mithilfe von Azure-Blobs, Tabellen, Warteschlangen und Dateien.

[Azure SQL-Datenbank](/azure/sql-database/)&mdash;wird beschrieben, wie die Verbindung mit Azure SQL-Datenbank, eine relationale Datenbank als Dienst.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;beschreibt die Tools, die das Design, durchsuchen, testen und Bereitstellen von Daten verbundenen Anwendungen und Datenbanken zu vereinfachen.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;beschreibt die ADO.NET-Architektur und Verwendung der ADO.NET-Klassen zum Verwalten von Anwendungsdaten und interagieren mit Datenquellen und XML.

[ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)&mdash;enthält Informationen zum Erstellen von datenanwendungen, die Entwicklern zur Programmierung für ein konzeptionelles Modell statt direkt für eine relationale Datenbank ermöglichen.

[WCF Data Services 4.5](/dotnet/framework/data/wcf/index)&mdash;beschreibt, wie [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] Datendienste im Internet oder Intranet bereitstellen, die Implementierung der [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

[Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)&mdash;enthält Links zu Themen, die allgemeine Funktionsweise von Daten in Office-Projektmappen erläutern. Dazu gehören Informationen über schemaorientierte Programmierung, Datenzwischenspeicherung und serverseitigen Datenzugriff.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;beschreibt die Abfragefunktionen, die in c# und Visual Basic sowie das allgemeine Abfragemodell für relationale Datenbanken, XML-Dokumente, Datasets und speicherinterne Auflistungen integriert.

[XML-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;erläutert arbeiten mit XML-Daten, Debuggen von XSLT, .NET Framework-XML-Funktionen und die Architektur der XML-Abfrage.

[XML-Dokumente und Daten](/dotnet/standard/data/xml/index)&mdash;bietet eine Übersicht über eine umfassende und integrierte Gruppe von Klassen, die mit XML-Dokumenten und-Daten in .NET Framework eingesetzt.
