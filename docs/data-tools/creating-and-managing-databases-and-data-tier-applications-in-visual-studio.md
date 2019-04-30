---
title: Datenbankprojekte und DAC-Projekte
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2a86d9511e470c9a810ff58e80e4cae1f9a0cb11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567239"
---
# <a name="database-projects-and-data-tier-applications"></a>Datenbankprojekte und Data-Tier-Anwendungen

Können Sie zum Erstellen neuer Datenbanken, Datenbankprojekte neue datenebenenanwendungen (DACs), und Aktualisieren von vorhandenen Datenbanken und Data-Tier-Anwendungen. Sowohl für Datenbankprojekte als auch für DAC-Projekten können Sie Version Control "und" Project-Management-Techniken auf Ihrer Datenbankentwicklung zu ähnelt der Vorgehensweise anwenden, dass Sie diese Techniken auf verwaltetem oder systemeigenem Code anwenden. Sie können Ihre Entwicklungsteams, die Änderungen an Datenbanken und Datenbank-Server zu verwalten, indem Sie erstellen ein DAC-Projekt, Datenbankprojekt oder einem Serverprojekt, und platzieren es unter Versionskontrolle. Mitglieder Ihres Teams können dann Dateien auschecken zu machen, erstellen und Testen von Änderungen in einer isolierten Entwicklungsumgebung oder Sandbox, bevor sie mit dem Team freigeben. Damit können die Codequalität zu gewährleisten, kann Ihr Team Fertig stellen und alle Änderungen für eine bestimmte Version der Datenbank in einer Stagingumgebung zu testen, bevor Sie die Änderungen in der produktionsumgebung bereitstellen.

Eine Liste der Datenbankfunktionen ein, die von Data-Tier-Anwendungen unterstützt werden, finden Sie unter [DAC-Unterstützung für SQL Server-Objekte](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Wenn Sie Funktionen in Ihrer Datenbank, die von Data-Tier-Anwendungen nicht unterstützt werden verwenden, sollten Sie stattdessen ein Datenbankprojekt zum Verwalten von Änderungen mit Ihrer Datenbank verwenden.

## <a name="common-high-level-tasks"></a>Allgemeine Aufgaben

| Übergeordnete Aufgabe | Unterstützender Inhalt |
| - | - |
| **Starten Sie die Entwicklung einer Anwendung von datenebenenanwendungen:** Das Konzept einer datenebenenanwendung (DAC) wurde mit SQL Server 2008 eingeführt. Eine DAC enthält die Definition für eine SQL Server-Datenbank und die unterstützenden Instanzobjekte, die von einem Client / Server oder eine 3-Ebenen-Anwendung verwendet werden. Eine DAC enthält Datenbankobjekte, z. B. Tabellen und Sichten, zusammen mit Instanz-Entitäten, z. B. Anmeldenamen. Sie können Visual Studio verwenden, um ein DAC-Projekt erstellen, eine DAC-Paketdatei erstellen und senden die DAC-Paketdatei an einen Datenbankadministrator für die Bereitstellung auf einer Instanz von SQL Server-Datenbank-Engine. | - [Datenschichtanwendungen](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Ausführen von iterativen-Datenbankentwicklung:** Entwickler können Teile des Projekts Auschecken und aktualisieren sie in einer isolierten Entwicklungsumgebung. Mithilfe dieser Art von Umgebung zu verwenden, können Sie Ihre Änderungen testen, ohne Auswirkungen auf andere Mitglieder des Teams. Nachdem die Änderungen abgeschlossen sind, überprüfen Sie die Dateien wieder in die Versionskontrolle, in denen andere Teammitglieder können Ihre Änderungen zu erhalten und erstellen und auf einem Testserver bereitstellen. | - [Projektorientierte Offlinedatenbankentwicklung (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Transact-SQL-Debugger (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Erstellen von Prototypen, Überprüfen von Testergebnissen, und Ändern von Datenbankskripts und Objekten:** Sie können den Transact-SQL-Editor verwenden, eine der folgenden allgemeinen Aufgaben ausführen. | - [Abfrage- und Text-Editoren (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)