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
ms.openlocfilehash: b793789e092b46f14db397c1f8aef4e98544f856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851682"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Erstellen und Verwalten von Datenbanken und Datenschichtanwendungen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WICHTIG]
> Die Datenbankprojekte, die in früheren Versionen von enthalten waren, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] werden jetzt in-Tools bereitgestellt [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] . Weitere Informationen finden Sie unter [SQL Server Developer Tools](https://msdn.microsoft.com/library/hh272686(VS.103).aspx).

 Sie können Datenbankprojekte zum Erstellen neuer Datenbanken, neuer Datenebenenanwendungen (DACs) und zum Aktualisieren vorhandener Datenbanken und Datenebenenanwendungen verwenden. Sowohl Datenbankprojekte als auch DAC-Projekte ermöglichen es Ihnen, Versionskontrolle und Projekt Verwaltungsverfahren auf die Datenbankentwicklung anzuwenden, ähnlich wie Sie diese Techniken auf verwalteten oder systemeigenen Code anwenden. Sie können dem Entwicklungsteam dabei helfen, Änderungen an Datenbanken und Datenbankservern zu verwalten, indem Sie ein *DAC-Projekt*, ein *Datenbankprojekt*oder ein *Server Projekt* erstellen und es in die Versionskontrolle versetzen. Mitglieder des Teams können dann Dateien Auschecken, um Änderungen in einer *isolierten Entwicklungsumgebung*oder in einem Sandkasten auszuführen, zu erstellen und zu testen, bevor Sie Sie für das Team freigeben. Um die Codequalität zu gewährleisten, kann Ihr Team alle Änderungen für eine bestimmte Version der Datenbank in einer Stagingumgebung abschließen und testen, bevor Sie die Änderungen in der Produktionsumgebung bereitstellen.

 Eine Liste der Datenbankfunktionen, die von Datenebenenanwendungen unterstützt werden, finden Sie unter Features, die in Datenebenenanwendungen auf der Microsoft [-Website unterstützt](https://msdn.microsoft.com/library/ee362013(VS.100).aspx) werden. Wenn Sie Funktionen in der Datenbank verwenden, die nicht von Datenebenenanwendungen unterstützt werden, sollten Sie stattdessen ein Datenbankprojekt verwenden, um Änderungen an der Datenbank zu verwalten.

## <a name="common-high-level-tasks"></a>Allgemeine allgemeine Aufgaben

|Allgemeine Aufgabe|Hilfreiche Themen|
|----------------------|------------------------|
|**Beginnen Sie mit der Entwicklung einer Datenebenenanwendung:** Eine DAC ist ein neues, mit eingeführte Konzept [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] , das die Definition für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datenbank und die unterstützenden Instanzobjekte enthält, die von einer Client-oder einer Anwendung mit drei Ebenen verwendet werden. Eine DAC enthält Datenbankobjekte, z. b. Tabellen und Sichten, sowie instanzentitäten, z. b. Anmeldungen. Sie können verwenden, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] um ein DAC-Projekt zu erstellen, eine DAC-Paketdatei zu erstellen und diese DAC-Paketdatei an einen Datenbankadministrator zu senden, um Sie auf einer Instanz der Datenbank-Engine bereitzustellen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-   [Erstellen und Verwalten von Datenebenenanwendungen](https://msdn.microsoft.com/library/ee361996(VS.100).aspx) (Microsoft-Website)<br />-   [SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(SQL.110).aspx)|
|**Ausführen einer iterativen Datenbankentwicklung:** Wenn Sie ein Entwickler oder Tester sind, checken Sie Teile des Projekts aus und aktualisieren Sie dann in einer isolierten Entwicklungsumgebung. Mit dieser Art von Umgebung können Sie Ihre Änderungen testen, ohne dass sich dies auf andere Mitglieder des Teams auswirkt. Nachdem die Änderungen vorgenommen wurden, überprüfen Sie die Dateien wieder in die Versionskontrolle, wo andere Teammitglieder ihre Änderungen abrufen und auf einem Testserver bereitstellen können.|-   [Abfrage-und Text-Editoren (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (Microsoft-Website)<br />-   [Transact-SQL-Debugger](https://msdn.microsoft.com/library/cc645997(SQL.110).aspx) (Microsoft-Website)|
|**Prototypen, überprüfen von Testergebnissen und Ändern von Daten Bank Skripts und Objekten:** Sie können den [!INCLUDE[tsql](../includes/tsql-md.md)] Editor verwenden, um eine dieser allgemeinen Aufgaben auszuführen.|-   [Abfrage-und Text-Editoren (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (Microsoft-Website)|

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
