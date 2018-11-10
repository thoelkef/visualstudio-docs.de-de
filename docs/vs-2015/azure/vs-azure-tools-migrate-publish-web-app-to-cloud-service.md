---
title: Wie Sie migrieren und Veröffentlichen einer Webanwendung auf Azure-Clouddienst aus Visual Studio | Microsoft-Dokumentation
description: Informationen Sie zum Migrieren und veröffentlichen Ihre Webanwendung in Azure-Clouddienst mit Visual Studio
author: ghogen
manager: douge
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: c122b54a4e22285678d13213cc73d6492baba629
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002068"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Vorgehensweise: Migrieren und Veröffentlichen einer Webanwendung auf Azure-Clouddienst aus Visual Studio

Um die Vorteile der Hostingdienste und Skalierbarkeit von Azure nutzen, empfiehlt es sich um migrieren und Bereitstellen der Webanwendung in Azure Cloud Services. Es sind nur minimale Änderungen erforderlich. Dieser Artikel behandelt die Bereitstellung in Clouddiensten nur; App Service finden Sie unter [bereitstellen eine Web-app in Azure App Service](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Diese Migration wird nur für bestimmte Projekte ASP.NET, Silverlight, WCF und WCF-Workflows unterstützt. Es ist für ASP.NET Core-Projekten nicht unterstützt. Finden Sie unter [unterstützte Projektvorlagen](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Migrieren eines Projekts zu Clouddiensten

1. Mit der rechten Maustaste in des Webanwendungsprojekts, und wählen Sie **konvertieren > in Microsoft Azure-Clouddienstprojekt konvertieren**. (Beachten Sie, dass dieser Befehl nicht angezeigt wird, wenn Sie bereits über ein Webrollenprojekt in der Projektmappe verfügen.)
1. Visual Studio erstellt ein clouddienstprojekt in der Projektmappe, die die erforderliche Webrolle enthält. Der Name dieses Projekts ist identisch, als Ihres Anwendungsprojekts mit plus das Suffix `.Azure`.
1. Außerdem wird von Visual Studio die **lokale Kopie** Eigenschaft auf "true" für alle Assemblys, die für MVC 2, MVC 3, MVC 4 und Silverlight-Geschäftsanwendungen erforderlich sind. Diese Eigenschaft fügt diese Assemblys dem Dienstpaket, die für die Bereitstellung verwendet wird.

   > [!Important]
   > Wenn Sie haben andere Assemblys oder Dateien, die für diese Webanwendung erforderlich sind, müssen Sie die Eigenschaften für diese Dateien manuell festlegen. Weitere Informationen zum Festlegen dieser Eigenschaften finden Sie unter [einschließen von Dateien in das Dienstpaket](#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Fehler und Warnungen

Geben alle Warnungen oder Fehler, die auftreten, Probleme zu beheben, bevor die Bereitstellung in Azure, wie z.B. fehlende Assemblys.

Wenn Sie Ihre Anwendung erstellen, sie lokal mit dem Serveremulator ausführen oder in Azure veröffentlichen, kann der Fehler angezeigt: "der angegebene Pfad und/oder Dateiname sind zu lang." Dieser Fehler weist darauf hin, dass der Name der vollqualifizierte Azure-Projekt als 146 Zeichen ist. Um das Problem zu beheben, verschieben Sie die Projektmappe in einen anderen Ordner mit einem kürzeren Pfad ein.

Weitere Informationen dazu, wie Sie alle Warnungen als Fehler behandelt werden, finden Sie unter [Konfigurieren eines Azure-Clouddienstprojekts mit Visual Studio](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Lokales Testen der migration

1. In Visual Studio **Projektmappen-Explorer**mit der rechten Maustaste auf das hinzugefügte clouddienstprojekt, und wählen Sie **als Startprojekt festlegen**.
1. Wählen Sie **Debuggen > Debuggen starten** (F5), um die Azure-Debugumgebung zu starten. Diese Umgebung wird insbesondere die Emulation verschiedener Azure-Dienste.

### <a name="use-an-azure-sql-database-for-your-application"></a>Verwenden von Azure SQL-Datenbank für Ihre Anwendung

Wenn Sie eine Verbindungszeichenfolge für Ihre Webanwendung, die eine lokalen SQL Server-Datenbank verwendet verfügen, müssen Sie stattdessen Migrieren von der Datenbank in Azure SQL-Datenbank und Aktualisieren der Verbindungszeichenfolge. Anleitung bei diesem Prozess finden Sie in den folgenden Themen:

- [SQL Server-Datenbankmigration zu SQL-Datenbank in der cloud](/azure/sql-database/sql-database-cloud-migrate)
- [Verwenden von .NET (C#) mit Visual Studio zum Verbinden und Abfragen und Azure SQL-Datenbank](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Die Anwendung in Azure-Clouddienst veröffentlichen

1. Erstellen die erforderlichen Cloud-Dienst und Speicherkonten im Azure-Abonnement wie im [veröffentlichen und Bereitstellen einer Azure-Anwendung aus Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md).
1. Klicken Sie in Visual Studio mit der rechten Maustaste in des Anwendungsprojekts, und wählen **in Microsoft Azure veröffentlichen...**  (Dies ist der Befehl "Publish..." unterscheiden.).
1. In der **Azure-Anwendung veröffentlichen** , das angezeigt wird, melden Sie sich mit dem Konto mit Ihrem Azure-Abonnement, und wählen Sie **Weiter >**.
1. In der **Einstellungen > Allgemeine Einstellungen** wählen den Ziel-Cloud-Dienst über die **Cloud-Dienst** Dropdown Liste zusammen mit der gewünschten Umgebung und Konfigurationen. 
1. In **Einstellungen > Erweiterte Einstellungen**, wählen Sie den Storage-Konto zu verwenden, und wählen Sie dann **Weiter >**.
1. In **Diagnose**, wählen Sie, ob Informationen an Application Insights gesendet.
1. Wählen Sie **Weiter >** um eine Zusammenfassung anzuzeigen, wählen Sie dann **veröffentlichen** Bereitstellung zu starten.
1. Visual Studio öffnet ein Aktivitätsprotokollfenster, in dem Sie den Status nachverfolgen können:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (Optional) Um den Bereitstellungsprozess abzubrechen, mit der rechten Maustaste in des Zeilenelement im Aktivitätsprotokoll, und wählen Sie **Abbrechen und entfernen**. Mit diesem Befehl wird der Bereitstellungsprozess beendet und löscht die bereitstellungsumgebung aus Azure. Hinweis: um die Entfernung der bereitstellungsumgebung, nachdem er bereitgestellt wurde, verwenden Sie die [Azure-Portal](https://portal.azure.com).
1. (Optional) Nach dem Starten der Rolleninstanzen zeigt Visual Studio automatisch der bereitstellungsumgebung im der **Server-Explorer > Cloud Services** Knoten. Von hier aus können Sie den Status der einzelnen Rolleninstanzen anzeigen.
1. Wählen Sie Ihre Anwendung nach der Bereitstellung den Zugriff auf den Pfeil neben der Bereitstellung, wenn der Status **abgeschlossen** wird in der **Azure-Aktivitätsprotokoll** zusammen mit der URL. Finden Sie die folgende Tabelle enthält die Details dazu, wie Sie einen bestimmten Typ von Web-Anwendung in Azure zu starten.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Mit dem Serveremulator und Starten der Anwendung in Azure

Alle Anwendungstypen können gestartet werden, in einem Browser, die mit Visual Studio-Debugger verbunden ist, dazu **Debuggen > Debuggen starten** (F5). Bei einem Projekt leere ASP.NET-Webanwendung müssen Sie zunächst Hinzufügen einer `.aspx` auf der Seite Ihrer Anwendung, und legen Sie es als Startseite für Ihr Webprojekt.

Die folgende Tabelle enthält Details zum Starten der Anwendung in Azure:

   | Webanwendungstyp | In Azure ausgeführt wird |
   | --- | --- | --- |
   | ASP.NET-Webanwendung<br/>(einschließlich MVC 2, MVC 3, MVC 4) | Wählen Sie die URL in die **Bereitstellung** auf der Registerkarte die **Azure-Aktivitätsprotokoll**. |
   | Leere ASP.NET-WEBANWENDUNG | Wenn Sie ein Standardwert ist `.aspx` auf der Seite Ihrer Anwendung, wählen Sie die URL in die **Bereitstellung** auf der Registerkarte die **Azure-Aktivitätsprotokoll**. Geben Sie zum Navigieren zu einer anderen Seite in einem Browser eine URL im folgenden Format ein: `<deployment_url>/<page_name>.aspx` |
   | Silverlight-Anwendung<br/>Silverlight-Geschäftsanwendung<br/>Silverlight-Navigationsanwendung | Navigieren Sie zu der spezifischen Seite für Ihre Anwendung mithilfe der folgende URL-Format: `<deployment_url>/<page_name>.aspx` |
    WCF-Dienstanwendung<br/>WCF-Workflowdienstanwendung | Legen Sie die `.svc` Datei als Startseite für Ihr WCF-Dienst-Projekt. Navigieren Sie dann auf `<deployment_url>/<service_file>.svc` |
   | ASP.NET Dynamic Entities<br/>ASP.NET Dynamic Data-Linq to SQL | Aktualisieren Sie die Verbindungszeichenfolge an, wie im nächsten Abschnitt beschrieben. Navigieren Sie zum `<deployment_url>/<page_name>.aspx`. Für Linq to SQL müssen Sie eine Azure SQL-Datenbank verwenden. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Aktualisieren einer Verbindungszeichenfolge für ASP.NET Dynamic Entities

1. Erstellen Sie eine SQL Azure-Datenbank für eine ASP.NET Dynamic Entities-Webanwendung, wie weiter oben in (#use-an-azuresql-database-for-your-application) beschrieben.
1. Fügen Sie die Tabellen und Felder, die Sie für diese Datenbank aus dem Azure-Portal benötigen.
1. Geben Sie eine Verbindungszeichenfolge in der `web.config` Datei mit dem folgenden Format ein, und speichern Sie die Datei:

    ```xml
    <addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

    Update der *"ConnectionString"* -Wert mit der ADO.NET-Verbindungszeichenfolge für die SQL Azure-Datenbank wie folgt:

    ```xml
    XMLCopy<addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Unterstützte Projektvorlagen

Anwendungen, die migriert und in Clouddiensten veröffentlicht werden können, müssen eine der Vorlagen in der folgenden Tabelle verwenden. ASP.NET Core wird nicht unterstützt.

| Vorlagengruppe | Projektvorlage |
| --- | --- |
| Web | ASP.NET Web-Anwendung ((.NET Framework) |
| Web | ASP.NET MVC 2-Webanwendung |
| Web | ASP.NET MVC 3-Webanwendung |
| Web | ASP.NET MVC 4-Webanwendung |
| Web | Leere ASP.NET-WEBANWENDUNG (oder Website) |
| Web | Leere ASP.NET MVC 2-Webanwendung |
| Web | ASP.NET Dynamic Data Entities-Webanwendung |
| Web | ASP.NET Dynamic Data-Linq to SQL-Web-Anwendung |
| Silverlight | Silverlight-Anwendung |
| Silverlight | Silverlight-Geschäftsanwendung |
| Silverlight | Silverlight-Navigationsanwendung |
| WCF | WCF-Dienstanwendung |
| WCF | WCF-Workflowdienstanwendung |
| Workflow | WCF-Workflowdienstanwendung |

## <a name="next-steps"></a>Nächste Schritte

- [Veröffentlichen und Bereitstellen einer Azure-Anwendung aus Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Einrichten benannter Authentifizierungsanmeldeinformationen](vs-azure-tools-setting-up-named-authentication-credentials.md).
