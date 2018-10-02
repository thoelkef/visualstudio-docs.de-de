---
title: Erstellen und Verwalten von Datenbanken und Data-Tier-Anwendungen in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ea5370349204765932baed828ffb9c9332b088f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521502"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Erstellen und Verwalten von Datenbanken und Data-Tier-Anwendungen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [erstellen und Verwalten von Datenbanken und datenebenenanwendungen](https://docs.microsoft.com/visualstudio/data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio).  
  
  
WICHTIG]
>  Die Datenbankprojekte, die in früheren Versionen von enthalten waren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] stehen nun in [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] Tools. Weitere Informationen finden Sie unter [SQL Server Developer Tools](http://go.microsoft.com/fwlink/?LinkId=228126).  
  
 Können Sie zum Erstellen neuer Datenbanken, Datenbankprojekte neue datenebenenanwendungen (DACs), und Aktualisieren von vorhandenen Datenbanken und Data-Tier-Anwendungen. Sowohl für Datenbankprojekte als auch für DAC-Projekten können Sie Version Control "und" Project-Management-Techniken auf Ihrer Datenbankentwicklung zu ähnelt der Vorgehensweise anwenden, dass Sie diese Techniken auf verwaltetem oder systemeigenem Code anwenden. Sie können Ihr Entwicklungsteam, das Verwalten von Änderungen an Datenbanken und Datenbankserver durch Erstellen einer *DAC-Projekt*, *Datenbankprojekt*, oder ein *Serverprojekt* und Versionskontrolle. Mitglieder Ihres Teams können dann sehen Sie sich zu machen, erstellen und Testen von Änderungen in Dateien eine *isolierten Entwicklungsumgebung*, oder, bevor sie mit dem Team freigeben. Damit können die Codequalität zu gewährleisten, kann Ihr Team Fertig stellen und alle Änderungen für eine bestimmte Version der Datenbank in einer Stagingumgebung zu testen, bevor Sie die Änderungen in der produktionsumgebung bereitstellen.  
  
 Eine Liste der Datenbankfunktionen ein, die von Data-Tier-Anwendungen unterstützt werden, finden Sie unter [-Funktionen in Datenebenenanwendungen unterstützt](http://go.microsoft.com/fwlink/?LinkId=164239) auf der Microsoft-Website. Wenn Sie Funktionen in Ihrer Datenbank, die von Data-Tier-Anwendungen nicht unterstützt werden verwenden, sollten Sie stattdessen ein Datenbankprojekt zum Verwalten von Änderungen mit Ihrer Datenbank verwenden.  
  
## <a name="common-high-level-tasks"></a>Allgemeine Aufgaben  
  
|Übergeordnete Aufgabe|Unterstützender Inhalt|  
|----------------------|------------------------|  
|**Starten Sie die Entwicklung einer Anwendung von datenebenenanwendungen:** eine DAC ist ein neues Konzept eingeführt, mit [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] , enthält die Definition für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank und die unterstützenden Instanzobjekte, die von einem Client / Server oder 3 Ebenen verwendet werden die Anwendung. Eine DAC enthält Datenbankobjekte, z. B. Tabellen und Sichten, zusammen mit Instanz-Entitäten, z. B. Anmeldenamen. Sie können [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] um ein DAC-Projekt zu erstellen, eine DAC-Paketdatei erstellen und senden Sie die DAC-Paketdatei an einen Datenbankadministrator für die Bereitstellung auf einer Instanz von der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datenbank-Engine.|-   [Erstellen und Verwalten von Datenebenenanwendungen](http://go.microsoft.com/fwlink/?LinkId=160741) (Microsoft-Website)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Ausführen von iterativen Datenbankentwicklung:** , wenn Sie ein Entwickler oder Tester sind, wird Sie Teile des Projekts Auschecken und aktualisieren Sie diese in einer isolierten Entwicklungsumgebung. Mithilfe dieser Art von Umgebung zu verwenden, können Sie Ihre Änderungen testen, ohne Auswirkungen auf andere Mitglieder des Teams. Nachdem die Änderungen abgeschlossen sind, überprüfen Sie die Dateien wieder in die Versionskontrolle, in denen andere Teammitglieder können Ihre Änderungen zu erhalten und erstellen und auf einem Testserver bereitstellen.|-   [Abfrage- und Text-Editoren (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft-Website)<br />-   [Transact-SQL-Debugger](http://go.microsoft.com/fwlink/?LinkId=227324) (Microsoft-Website)|  
|**Erstellen von Prototypen, Überprüfen der Ergebnisse zu erzielen, und Ändern von Datenbankskripts und Objekten zu testen:** können Sie die [!INCLUDE[tsql](../includes/tsql-md.md)] -Editor, um eine der folgenden allgemeinen Aufgaben ausführen.|-   [Abfrage- und Text-Editoren (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft-Website)|  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

