---
title: 'Fehler: Ein Transact-SQL-Ausführung wurde ohne Debuggen beendet. | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/08/2018
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
ms.openlocfilehash: 0efb83f6b6cbebc255f6f47c30e3934d74de7870
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348999"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Fehler: Das Ausführen von Transact-SQL wurde ohne Debuggen beendet

Dieser Fehler tritt auf, wenn Sie versuchen, eine Transact-SQL oder eine CLR-Prozedur Debuggen und der Debugger keine Debugmeldungen vom SQL Server erhält.  
  
Dieses Problem kann aufgrund von Netzwerkproblemen oder zu Problemen auf dem SQL Server sein, aber die wahrscheinlichste Ursache ist ein Berechtigungsproblem vorliegt.  
  
Zwei Konten sind beteiligt:  
  
- Das Anwendungskonto ist das Benutzerkonto, unter dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird.  
  
- Das Verbindungskonto ist die Identität, mit der die Verbindung zu SQL Server hergestellt wird. Dieses Konto ist nicht unbedingt identisch mit der Identität, die Visual Studio ausgeführt wird, als ob die Verbindung mit SQL-Authentifizierung verwendet wird.  
  
  SQL-Debuggen erfordert, dass das Konto muss mit dem Verbindungskonto übereinstimmen oder Mitglied der Rolle Sysadmin.  
  
  Wenn Sie einen SQL-Kontonamen wie sa verwenden, muss das Anwendungskonto auf dem SQL Server als Systemadministrator eingerichtet werden. Standardmäßig sind Administratoren auf dem Computer, den SQLServer ausgeführt wird, auf SQL Server-Systemadministratoren.  
  
  So können Sie diesen Fehler korrigieren:  
  
  - Überprüfen Sie die Berechtigungseinstellungen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von SQL Server-Berechtigungen zum Debugging](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
  - Stellen Sie sicher, dass SQL-Debuggen ordnungsgemäß eingerichtet ist.  
  
  - Weitere Informationen erhalten Sie vom Netzwerk- oder Datenbankadministrator.  
  
## <a name="see-also"></a>Siehe auch

- [Einrichten von SQL-Debugging](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Vorgehensweise: Festlegen von SQL Server-Berechtigungen für das Debuggen](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)