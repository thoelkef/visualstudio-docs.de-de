---
title: "Creating and Managing Databases and Data-tier Applications in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing change, databases"
  - "database features of Visual Studio, managing change"
  - "databases, managing change"
  - "managing change, database servers"
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 37
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating and Managing Databases and Data-tier Applications in Visual Studio
> [!IMPORTANT]
>  Die Datenbankprojekte, die in früheren Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enthalten waren, werden jetzt in [!INCLUDE[sql_Denali_long](../data-tools/includes/sql_denali_long_md.md)] Tools bereitgestellt.  Weitere Informationen finden Sie unter [SQL Server\-Entwicklertoole](http://go.microsoft.com/fwlink/?LinkId=228126).  
  
 Sie können mithilfe von Datenbankprojekten neue Datenbanken und neue Datenebenenanwendungen \(DACs\) erstellen sowie vorhandene Datenbanken und Datenebenenanwendungen aktualisieren.  Sowohl Datenbankprojekte als auch DAC\-Projekte ermöglichen Ihnen, Verfahren der Versionskontrolle und Projektverwaltung auf die gleiche Weise auf die Datenbankentwicklung anzuwenden, wie Sie diese auf verwalteten oder systemeigenen Code anwenden.  Sie können die Verwaltung von Änderungen an Datenbanken und Datenbankservern durch das Entwicklungsteam vereinfachen, indem Sie ein *DAC\-Projekt*, ein *Datenbankprojekt* oder ein *Serverprojekt* erstellen und es der Versionskontrolle unterstellen.  Mitglieder des Teams können dann Dateien auschecken, um Änderungen in einer *isolierten Entwicklungsumgebung* durchzuführen, die auch als Sandbox bezeichnet wird, sowie einen entsprechenden Build zu erstellen und zu testen, bevor sie für das Team freigegeben werden.  Um die Codequalität sicherzustellen, kann das Team alle Änderungen für eine bestimmte Version der Datenbank in einer Stagingumgebung fertig stellen und testen, bevor Sie die Änderungen für die Produktion bereitstellen.  
  
 Eine Liste der Datenbankfunktionen, die von Anwendungen unterstützt werden, finden [Funktionen unterstützt in Anwendungen auf Datenebene](http://go.microsoft.com/fwlink/?LinkId=164239) Sie auf der Microsoft\-Website.  Wenn Sie in der Datenbank Funktionen verwenden, die von Anwendungen auf Datenebene nicht unterstützt werden, sollten Sie stattdessen Änderungen an der Datenbank mithilfe eines Datenbankprojekts verwalten.  
  
## Häufige übergeordnete Aufgaben  
  
|Übergeordnete Aufgabe|Unterstützender Inhalt|  
|---------------------------|----------------------------|  
|**Beginnen der Entwicklung einer Datenebenenanwendung**: Eine Datenebenenanwendung \(DAC\) ist ein neues Konzept, das mit [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] eingeführt wurde und das die Definition für eine [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]\-Datenbank sowie die unterstützenden Instanzobjekte enthält, die von einer Client\-\/Server\-Anwendung oder 3\-Ebenen\-Anwendung verwendet werden.  Eine DAC enthält Datenbankobjekte, z. B. Tabellen und Ansichten, sowie Instanzentitäten, z. B. Anmeldungen.  Sie können mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein DAC\-Projekt erstellen, eine DAC\-Paketdatei erstellen und die DAC\-Paketdatei an einen Datenbankadministrator für die Bereitstellung in einer Instanz des [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]\-Datenbankmoduls senden.|-   [Erstellen und Verwalten von Datenebenenanwendungen](http://go.microsoft.com/fwlink/?LinkId=160741) \(Microsoft\-Website\)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Ausführen von iterativer Datenbankentwicklung**: Wenn Sie ein Entwickler oder Tester sind, checken Sie Teile des Projekts aus und aktualisieren sie dann in einer isolierten Entwicklungsumgebung.  Mit diesen Typ der Umgebung verwenden, können Sie die Änderungen testen, ohne andere Teammitglieder zu beeinflussen.  Nachdem die Änderungen abgeschlossen wurden, checken Sie die Dateien wieder in die Versionskontrolle ein, sodass andere Teammitglieder die Änderungen abrufen und sie auf einem Testserver als Build erstellen und bereitstellen können.|-   [Abfrage und Text\-Editoren \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Microsoft\-Website\)<br />-   [Transact\-SQL\-Debugger](http://go.microsoft.com/fwlink/?LinkId=227324) \(Microsoft\-Website\)|  
|**Prototyperstellung, Überprüfen der Testergebnisse und Ändern von Datenbankskripts und \-objekten**: Sie können jede dieser häufigen Aufgaben mithilfe des [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)]\-Editors ausführen.|-   [Abfrage und Text\-Editoren \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Microsoft\-Website\)|