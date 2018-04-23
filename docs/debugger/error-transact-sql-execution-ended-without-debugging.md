---
title: 'Fehler: Ein Transact-SQL-Ausführung wurde ohne Debuggen beendet. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3ccb86621295bb102738e5154f30bd45c6db358
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Fehler: Das Ausführen von Transact-SQL wurde ohne Debuggen beendet
Dieser Fehler tritt auf, wenn Sie versuchen, eine Transact-SQL- oder SQL/CLR-Prozedur zu debuggen und der Debugger keine Debugmeldungen vom SQL-Server erhält.  
  
 Dies kann durch Netzwerkprobleme oder Probleme auf dem SQL-Server verursacht worden sein, aber die wahrscheinlichste Ursache ist ein Berechtigungsproblem.  
  
 Zwei Konten sind beteiligt:  
  
-   Das Anwendungskonto ist das Benutzerkonto, unter dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird.  
  
-   Das Verbindungskonto ist die Identität, mit der die Verbindung zu SQL Server hergestellt wird. Dies ist nicht notwendigerweise die gleiche Identität, unter der Visual Studio ausgeführt wird, wenn die Verbindung SQL-Authentifizierung verwendet.  
  
 SQL-Debuggen erfordert, dass das Anwendungskonto mit dem Verbindungskonto übereinstimmen muss oder Systemadministratorrechte hat.  
  
 Wenn Sie einen SQL-Benutzernamen wie sa verwenden, muss das Anwendungskonto auf dem SQL-Server als Systemadministrator eingerichtet sein. Standardmäßig sind Administratoren auf dem Computer, auf dem SQL Server ausgeführt wird, SQL Server-Systemadministratoren.  
  
 So können Sie diesen Fehler korrigieren:  
  
-   Überprüfen Sie die Berechtigungseinstellungen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von SQL Server-Berechtigungen zum Debugging](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Stellen Sie sicher, dass SQL-Debuggen ordnungsgemäß eingerichtet ist.  
  
-   Weitere Informationen erhalten Sie vom Netzwerk- oder Datenbankadministrator.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten von SQL-Debuggen](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Vorgehensweise: Festlegen von SQL Server-Berechtigungen für das Debuggen](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)