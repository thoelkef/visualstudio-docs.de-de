---
title: -Projekte, Server-Projekte und DAC-Projekte in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 8e599e1d309ab254c2b2d5a3a490c0cd912b8823
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Datenbankprojekte als auch Data-Tier-Anwendungen in Visual Studio  
Können Sie zum Erstellen neuer Datenbanken Datenbankprojekte neue datenebenenanwendungen (DACs), und vorhandene Datenbanken und datenebenenanwendungen zu aktualisieren. Sowohl für Datenbankprojekte als auch für DAC-Projekte ermöglichen es Ihnen Version Control und Projekt containerverwaltungstechniken auf Ihren entwicklungsvorhaben Datenbank im großen und ganzen genauso angewendet wird, diese Techniken auf verwaltetem oder systemeigenem Code angewendet werden. Helfen Sie dem Entwicklungsteam Verwalten von Änderungen an Datenbanken und Datenbankserver durch Erstellen einer *DAC-Projekt*, *Datenbankprojekt*, oder ein *Serverprojekt* und zu deren unter Versionskontrolle. Mitglieder Ihres Teams können dann Auschecken von Dateien zu machen, erstellen und Testen Sie die Änderungen in einer *isolierten Entwicklungsumgebung*, oder Sandkasten, bevor Sie das Team freigeben. Um die Qualität des Codes sicherzustellen, Ihr Team kann abgeschlossen und alle Änderungen für eine bestimmte Version der Datenbank in einer Stagingumgebung testen, bevor Sie die Änderungen in die Produktion bereitstellen.  
  
Eine Liste der Datenbankfunktionen ein, die von Data-Tier-Anwendungen unterstützt werden, finden Sie unter [unterstützte Funktionen in Data-Tier Applications](http://go.microsoft.com/fwlink/?LinkId=164239) auf der Microsoft-Website. Bei Verwendung von Funktionen in der Datenbank, die nicht von Data-Tier-Anwendungen unterstützt werden sollten Sie stattdessen ein Datenbankprojekt verwenden, um Änderungen auf Ihre Datenbank zu verwalten.  
  
## <a name="common-high-level-tasks"></a>Allgemeine Aufgaben  
  
|Übergeordnete Aufgabe|Unterstützender Inhalt|  
|----------------------|------------------------|  
|**Starten Sie die Entwicklung einer Data-Tier-Anwendung:** eine DAC ist ein neues Konzept eingeführt, mit [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] , enthält die Definition für eine [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] Datenbank und die unterstützenden Instanzobjekte, die von einem Client / Server- oder 3-Ebenen verwendet werden die Anwendung. Eine DAC enthält Datenbankobjekte, z. B. Tabellen und Sichten, zusammen mit der Instanz-Entitäten, z. B. Anmeldenamen. Sie können [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] um ein DAC-Projekt zu erstellen, eine DAC-Paketdatei erstellen und senden Sie die DAC-Paketdatei an einen Datenbankadministrator für die Bereitstellung in einer Instanz von der [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] -Datenbankmoduls.|-   [Erstellen und Verwalten von Data-Tier Applications](http://go.microsoft.com/fwlink/?LinkId=160741) (Microsoft-Website)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Ausführen von iterativen Datenbankentwicklung:** Wenn Sie ein Entwickler oder Tester sind, wird Sie Teile des Projekts Auschecken und aktualisieren Sie sie in einer isolierten Entwicklungsumgebung. Mithilfe dieser Art von Umgebung können Sie Ihre Änderungen testen, ohne Auswirkungen auf andere Mitglieder des Teams. Nachdem die Änderungen abgeschlossen sind, überprüfen Sie die Dateien wieder in die Versionskontrolle, in denen andere Teammitglieder sowohl die Änderungen zu erhalten und erstellen und bereitstellen können sie auf einem Testserver.|-   [Abfrage- und Text-Editoren (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft-Website)<br />-   [Transact-SQL-Debugger](http://go.microsoft.com/fwlink/?LinkId=227324) (Microsoft-Website)|  
|**Erstellen von Prototypen, überprüfen Testergebnisse, und Ändern von Datenbankskripts und Objekte:** können Sie die [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] -Editor, um diesen gemeinsamen Aufgaben ausführen.|-   [Abfrage- und Text-Editoren (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft-Website)|  
  
## <a name="see-also"></a>Siehe auch
[Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
