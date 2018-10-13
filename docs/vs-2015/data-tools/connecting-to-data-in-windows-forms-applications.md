---
title: Verbinden mit Daten in Windows Forms-Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- System.Data.SqlClient.SqlConnection
- System.Data.Odbc.OdbcConnection
- System.Data.OleDb.OleDbConnection
- System.Data.OracleClient.OracleConnection
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connection objects, tools for working with
- OleDbConnection class, ADO.NET connection objects
- databases [Visual Studio], connecting to
- data adapters, connections
- connection pooling, ADO.NET connections
- connection strings [Visual Studio], ADO.NET
- connection objects, types of
- dynamic properties, ADO.NET connections
- connections, about connections
- data [Visual Studio], connecting
- design-time connections
- connections, design-time
- TableAdapters, connections
- connection objects
- SqlConnection class, ADO.NET connection objects
- connecting to databases, ADO.NET connections
- transactions, ADO.NET
- database connections [Visual Studio], ADO.NET
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d8da35b32f3dd25bd7ed47b25f722c6b0aa21ac7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208948"
---
# <a name="connecting-to-data-in-windows-forms-applications"></a>Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bietet Tools zum Verbinden der Anwendung auf Daten aus vielen verschiedenen Quellen, z. B. Datenbanken, Webdienste und Objekte. Wenn Sie Datenentwurfstools in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verwenden, müssen Sie häufig nicht explizit ein Datenverbindungsobjekt für das Formular oder die Komponente erstellen. Das Verbindungsobjekt wird typischerweise erstellt, wenn Sie einen der Daten-Assistenten durchlaufen haben oder Datenobjekte auf das Formular ziehen. Um die Anwendung mit Daten in einer Datenbank, einem Webdienst oder einem Objekt zu verbinden, führen Sie die [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) dazu **neue Datenquelle hinzufügen** aus der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Das folgende Diagramm zeigt den standardmäßigen Ablauf der Vorgänge beim Verbinden von Daten mittels der Durchführung einer TableAdapter-Abfrage für das Abrufen von Daten und deren Anzeige im Formular in einer Windows-Anwendung.  
  
 ![Datenfluss in einer Clientanwendung](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 In manchen Situationen ist es praktisch, ein Verbindungsobjekt ohne die Unterstützung durch irgendein Datenentwurfstool zu erstellen. Informationen zum Erstellen programmgesteuerter Verbindungen finden Sie unter [Herstellen einer Verbindung mit einer Datenquelle](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e).  
  
> [!NOTE]
>  Weitere Informationen zur Verbindung von Webanwendungen mit Daten finden Sie unter [ASP.NET Data Access Content Map](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## <a name="walkthroughs-for-connecting-windows-forms-applications-to-data"></a>Exemplarische Vorgehensweisen für das Verbinden von Windows Forms-Anwendungen mit Daten  
 Die folgenden exemplarischen Vorgehensweisen enthalten Vorgehensweisen für das Verbinden von Daten mit Windows Forms-Anwendungen:  
  
-   [Exemplarische Vorgehensweise: Verbinden mit Daten in einer Datenbank (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)  
  
-   [Exemplarische Vorgehensweise: Herstellen einer Verbindung mit Daten in einer lokalen Datenbankdatei (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [Exemplarische Vorgehensweise: Verbinden mit Daten in einem Webdienst (Windows Forms)](http://msdn.microsoft.com/library/079fb9b0-c733-40c1-acd1-d0d68834354d)  
  
-   [Exemplarische Vorgehensweise: Verbinden mit Daten in Objekten (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)  
  
-   [Herstellen einer Verbindung mit Daten in einer Access-Datenbank (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## <a name="creating-connections"></a>Verbindungen erstellen  
 In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Verbindungen konfiguriert werden, mithilfe der **Verbindung hinzufügen/ändern** Dialogfeld. Die **Verbindung hinzufügen** Dialogfeld wird angezeigt, wenn Sie bearbeiten oder Erstellen von Verbindungen innerhalb der Daten-Assistenten oder [Server Explorer/Datenbank-Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) oder beim Bearbeiten von Verbindungseigenschaften in die **Eigenschaften** Fenster.  
  
 Datenverbindungen werden automatisch konfiguriert, wenn Sie eine der folgenden Aktionen durchführen.  
  
|Aktion|Beschreibung|  
|------------|-----------------|  
|Führen Sie die [Datenquellen-Assistenten](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).|Verbindungen werden konfiguriert, wenn der Pfad der Datenbank, in ausgewählt wird der **Assistenten zur Datenquellenkonfiguration**. Weitere Informationen finden Sie unter [How to: Connect to Data in a Database](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Führen Sie die [TableAdapter-Konfigurations-Assistenten](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8).|Verbindungen werden erstellt, in der **TableAdapter-Konfigurations-Assistenten**. Weitere Informationen finden Sie unter [erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Führen Sie die [Bearbeiten von TableAdapters](../data-tools/editing-tableadapters.md).|Verbindungen werden erstellt, in der **Konfigurations-Assistenten für TableAdapter-Abfragen**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md).|  
|Ziehen Sie Elemente aus der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf ein Formular oder die [Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282).|Verbindungsobjekte werden erstellt, wenn das Ziehen von Elementen aus der **Datenquellen** Fenster auf die **Windows Forms-Designer** oder **Component Designer**. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Hinzufügen neuer datenverbindungen zu [Server Explorer/Datenbank-Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d).|Datenverbindungen in **Server Explorer/Datenbank-Explorer** werden in der Liste der verfügbaren Verbindungen im Daten-Assistenten|  
  
## <a name="connection-strings"></a>Verbindungszeichenfolgen  
 Verbindungszeichenfolgen können in der kompilierten Anwendung oder in einer Anwendungskonfigurationsdatei gespeichert werden. Weitere Informationen finden Sie unter [Vorgehensweise: Speichern und Bearbeiten von Verbindungszeichenfolgen](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
## <a name="connection-information-and-security"></a>Verbindungsinformationen und Sicherheit  
 Weil das Öffnen einer Verbindung den Zugriff auf eine wichtige Ressource – eine Datenbank – beinhaltet, treten häufig Sicherheitsprobleme beim Konfigurieren und Arbeiten mit einer Verbindung auf.  
  
 Wie Sie die Anwendung und ihren Zugriff auf die Datenquelle sichern, hängt von der Architektur des Systems ab. In einer webbasierten Anwendung beispielsweise erhalten Benutzer üblicherweise anonymen Zugriff auf die Internetinformationsdienste (IIS) und geben deshalb keine Sicherheitsanmeldeinformationen an. In diesem Fall unterhält die Anwendung eigene Anmeldeinformationen und verwendet diese statt irgendwelcher spezifischer Benutzerinformationen für die Verbindung und den Zugriff auf die Datenbank.  
  
> [!IMPORTANT]
>  Das Speichern von Informationen über Verbindungszeichenfolgen wie z. B. das Kennwort kann die Sicherheit einer Anwendung beeinträchtigen. Die integrierte Sicherheit von Windows bietet eine sicherere Methode der Zugriffssteuerung für eine Datenbank. Weitere Informationen finden Sie unter [Protecting Connection Information (Schützen von Verbindungsinformationen)](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
 Im Intranet oder in Anwendungen mit mehreren Ebenen können Sie die integrierte Sicherheitsoption nutzen, die von Windows, IIS und SQL Server bereitgestellt wird. In diesem Modell werden die Authentifizierungsanmeldedaten für das lokale Netzwerk ebenfalls für den Zugriff auf Datenbankressourcen verwendet und in der Verbindungszeichenfolge kein ausdrücklicher Benutzername oder Kennwort gebraucht. Typischerweise werden Berechtigungen auf dem Datenbankservercomputer mithilfe von Gruppen ermöglicht, sodass man keine individuelle Berechtigung für jeden Benutzer braucht, der auf die Datenbank zuzugreifen kann. In diesem Modell müssen überhaupt keine Anmeldeinformationen gespeichert werden und es sind keine zusätzlichen Schritte erforderlich, um die Informationen der Verbindungszeichenfolge zu schützen.  
  
 Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Sichern von ADO.NET-Anwendungen](http://msdn.microsoft.com/library/005a1d43-6ee5-471e-ad98-1d30a44d49d5)  
  
-   [Mehr Sicherheit beim Datei- und Datenzugriff in Windows Forms](http://msdn.microsoft.com/library/3cd3e55b-2f5e-40dd-835d-f50f7ce08967)  
  
## <a name="design-time-connections-in-server-explorerdatabase-explorer"></a>Entwurfszeitverbindungen in Server-Explorer/Datenbank-Explorer  
 **Server-Explorer/Datenbank-Explorer** bietet eine Möglichkeit zum Erstellen von entwurfszeitverbindungen zu Datenquellen. Damit können Sie verfügbare Datenquellen durchsuchen; Informationen über die Tabellen, Spalten und andere Elemente anzeigen, die sie enthalten; und Datenbankelemente bearbeiten und erstellen.  
  
 Ihre Anwendung nicht direkt die Verbindungen, die in verfügbaren verwendet **Server Explorer/Datenbank-Explorer**. Diese Verbindungen werden von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] für die Arbeit an der Datenbank zur Entwurfszeit verwendet. Weitere Informationen finden Sie unter [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Z. B. zur Entwurfszeit können **Server Explorer/Datenbank-Explorer** um eine Verbindung mit einer Datenbank zu erstellen. Später, wenn ein Formular entwerfen, Sie können die Datenbank durchsuchen, wählen Sie Spalten aus einer Tabelle, und ziehen sie auf die [Dataset-Designer](../data-tools/creating-and-editing-typed-datasets.md). Dies erstellt eine [TableAdapter](../data-tools/tableadapter-overview.md) in Ihrem Dataset. Außerdem wird ein neues Verbindungsobjekt erstellt, das Teil des neuen TableAdapters ist.  
  
 Informationen über Entwurfszeitverbindungen werden unabhängig von einem speziellen Projekt oder einer bestimmten Lösung auf Ihrem lokalen Computer gespeichert. Aus diesem Grund werden, wenn Sie eine Verbindung zur Entwurfszeit bei der Arbeit in einer Anwendung eingerichtet haben, wird im **Server Explorer/Datenbank-Explorer** jedes Mal, wenn Sie beim Arbeiten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], solange der Server, der die Verbindung Verteilungspunkt verfügbar ist. Weitere Informationen finden Sie unter [Vorgehensweise: Verbinden mit einer Datenbank im Server-Explorer](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../includes/sqlobjectexplorer-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorgehensweise: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Exemplarische Vorgehensweise: Verbinden mit Daten in einer Datenbank (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [ASP.NET Data Access-Inhaltszuordnung](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)