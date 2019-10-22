---
title: Erstellen und Verwalten von Datenbanken und Datenebenenanwendungen
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d6ed13f2e21ea6b9da82eb47afefdd16088e71d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672463"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Erstellen und Verwalten von Datenbanken und Datenschichtanwendungen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WICHTIG]
> Die Datenbankprojekte, die in früheren Versionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] enthalten waren, werden jetzt in [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] Tools bereitgestellt. Weitere Informationen finden Sie unter [SQL Server Developer Tools](http://go.microsoft.com/fwlink/?LinkId=228126).

 Sie können Datenbankprojekte zum Erstellen neuer Datenbanken, neuer Datenebenenanwendungen (DACs) und zum Aktualisieren vorhandener Datenbanken und Datenebenenanwendungen verwenden. Sowohl Datenbankprojekte als auch DAC-Projekte ermöglichen es Ihnen, Versionskontrolle und Projekt Verwaltungsverfahren auf die Datenbankentwicklung anzuwenden, ähnlich wie Sie diese Techniken auf verwalteten oder systemeigenen Code anwenden. Sie können dem Entwicklungsteam dabei helfen, Änderungen an Datenbanken und Datenbankservern zu verwalten, indem Sie ein *DAC-Projekt*, ein *Datenbankprojekt*oder ein *Server Projekt* erstellen und es in die Versionskontrolle versetzen. Mitglieder des Teams können dann Dateien Auschecken, um Änderungen in einer *isolierten Entwicklungsumgebung*oder in einem Sandkasten auszuführen, zu erstellen und zu testen, bevor Sie Sie für das Team freigeben. Um die Codequalität zu gewährleisten, kann Ihr Team alle Änderungen für eine bestimmte Version der Datenbank in einer Stagingumgebung abschließen und testen, bevor Sie die Änderungen in der Produktionsumgebung bereitstellen.

 Eine Liste der Datenbankfunktionen, die von Datenebenenanwendungen unterstützt werden, finden Sie unter Features, die in Datenebenenanwendungen auf der Microsoft [-Website unterstützt](http://go.microsoft.com/fwlink/?LinkId=164239) werden. Wenn Sie Funktionen in der Datenbank verwenden, die nicht von Datenebenenanwendungen unterstützt werden, sollten Sie stattdessen ein Datenbankprojekt verwenden, um Änderungen an der Datenbank zu verwalten.

## <a name="common-high-level-tasks"></a>Allgemeine allgemeine Aufgaben

|Allgemeine Aufgabe|Unterstützender Inhalt|
|----------------------|------------------------|
|**Beginnen Sie mit der Entwicklung einer Datenebenenanwendung:** Eine DAC ist ein neues Konzept, das mit [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] eingeführt wurde, das die Definition für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datenbank und die unterstützenden Instanzobjekte enthält, die von einer Client-oder einer 3-Ebenen-Anwendung verwendet werden. Eine DAC enthält Datenbankobjekte, z. b. Tabellen und Sichten, sowie instanzentitäten, z. b. Anmeldungen. Sie können [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verwenden, um ein DAC-Projekt zu erstellen, eine DAC-Paketdatei zu erstellen und diese DAC-Paketdatei an einen Datenbankadministrator für die Bereitstellung auf einer Instanz der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datenbank-Engine zu senden.|-   [Erstellen und Verwalten von Datenebenenanwendungen](http://go.microsoft.com/fwlink/?LinkId=160741) (Microsoft-Website)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Ausführen einer iterativen Datenbankentwicklung:** Wenn Sie ein Entwickler oder Tester sind, checken Sie Teile des Projekts aus und aktualisieren Sie dann in einer isolierten Entwicklungsumgebung. Mit dieser Art von Umgebung können Sie Ihre Änderungen testen, ohne dass sich dies auf andere Mitglieder des Teams auswirkt. Nachdem die Änderungen vorgenommen wurden, überprüfen Sie die Dateien wieder in die Versionskontrolle, wo andere Teammitglieder ihre Änderungen abrufen und auf einem Testserver bereitstellen können.|-   [Abfrage-und Text-Editoren (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft-Website)<br />-   [Transact-SQL-Debugger](http://go.microsoft.com/fwlink/?LinkId=227324) (Microsoft-Website)|
|**Prototypen, überprüfen von Testergebnissen und Ändern von Daten Bank Skripts und Objekten:** Sie können den [!INCLUDE[tsql](../includes/tsql-md.md)]-Editor verwenden, um eine dieser allgemeinen Aufgaben auszuführen.|-   [Abfrage-und Text-Editoren (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft-Website)|

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
