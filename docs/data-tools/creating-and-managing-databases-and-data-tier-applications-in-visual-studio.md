---
title: Datenbankprojekten, Serverprojekten und DAC-Projekte in Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 03dca206f38d98c44e711e945f5d4015142f0af9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758406"
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Datenbankprojekte und Data-Tier-Anwendungen in Visual Studio
Können Sie zum Erstellen neuer Datenbanken, Datenbankprojekte neue datenebenenanwendungen (DACs), und Aktualisieren von vorhandenen Datenbanken und Data-Tier-Anwendungen. Sowohl für Datenbankprojekte als auch für DAC-Projekten können Sie Version Control "und" Project-Management-Techniken auf Ihrer Datenbankentwicklung zu ähnelt der Vorgehensweise anwenden, dass Sie diese Techniken auf verwaltetem oder systemeigenem Code anwenden. Sie können Ihre Entwicklungsteams, die Änderungen an Datenbanken und Datenbank-Server zu verwalten, indem Sie erstellen ein DAC-Projekt, Datenbankprojekt oder einem Serverprojekt, und platzieren es unter Versionskontrolle. Mitglieder Ihres Teams können dann Dateien auschecken zu machen, erstellen und Testen von Änderungen in einer isolierten Entwicklungsumgebung oder Sandbox, bevor sie mit dem Team freigeben. Damit können die Codequalität zu gewährleisten, kann Ihr Team Fertig stellen und alle Änderungen für eine bestimmte Version der Datenbank in einer Stagingumgebung zu testen, bevor Sie die Änderungen in der produktionsumgebung bereitstellen.

Eine Liste der Datenbankfunktionen ein, die von Data-Tier-Anwendungen unterstützt werden, finden Sie unter [-Funktionen in datenebenenanwendungen unterstützt](http://go.microsoft.com/fwlink/?LinkId=164239) auf der Microsoft-Website. Wenn Sie Funktionen in Ihrer Datenbank, die von Data-Tier-Anwendungen nicht unterstützt werden verwenden, sollten Sie stattdessen ein Datenbankprojekt zum Verwalten von Änderungen mit Ihrer Datenbank verwenden.

## <a name="common-high-level-tasks"></a>Allgemeine Aufgaben

|Übergeordnete Aufgabe|Unterstützender Inhalt|
|----------------------|------------------------|
|**Starten Sie die Entwicklung einer Anwendung von datenebenenanwendungen:** eine DAC ist ein neues Konzept eingeführt, mit [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] , enthält die Definition für eine [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] -Datenbank und die unterstützenden Instanzobjekte, die von einem Client / Server oder 3 Ebenen verwendet werden die Anwendung. Eine DAC enthält Datenbankobjekte, z. B. Tabellen und Sichten, zusammen mit Instanz-Entitäten, z. B. Anmeldenamen. Sie können Visual Studio verwenden, um ein DAC-Projekt erstellen, eine DAC-Paketdatei erstellen und senden die DAC-Paketdatei an einen Datenbankadministrator für die Bereitstellung auf einer Instanz von der [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] Datenbank-Engine.|-   [Erstellen und Verwalten von Datenebenenanwendungen](http://go.microsoft.com/fwlink/?LinkId=160741) (Microsoft-Website)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Ausführen von iterativen Datenbankentwicklung:** , wenn Sie ein Entwickler oder Tester sind, wird Sie Teile des Projekts Auschecken und aktualisieren Sie diese in einer isolierten Entwicklungsumgebung. Mithilfe dieser Art von Umgebung zu verwenden, können Sie Ihre Änderungen testen, ohne Auswirkungen auf andere Mitglieder des Teams. Nachdem die Änderungen abgeschlossen sind, überprüfen Sie die Dateien wieder in die Versionskontrolle, in denen andere Teammitglieder können Ihre Änderungen zu erhalten und erstellen und auf einem Testserver bereitstellen.|-   [Abfrage- und Text-Editoren (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft-Website)<br />-   [Transact-SQL-Debugger](http://go.microsoft.com/fwlink/?LinkId=227324) (Microsoft-Website)|
|**Erstellen von Prototypen, Überprüfen der Ergebnisse zu erzielen, und Ändern von Datenbankskripts und Objekten zu testen:** können Sie die [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] -Editor, um eine der folgenden allgemeinen Aufgaben ausführen.|-   [Abfrage- und Text-Editoren (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft-Website)|

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
