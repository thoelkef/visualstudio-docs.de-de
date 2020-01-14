---
title: 'Fehler: die Transact-SQL-Ausführung wurde ohne Debuggen beendet | Microsoft-Dokumentation'
ms.date: 11/08/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e86e24f775d8470b54ed7b9c54d27a5d3c1ee8da
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916305"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Fehler: Das Ausführen von Transact-SQL wurde ohne Debuggen beendet

Dieser Fehler tritt auf, wenn Sie versuchen, eine Transact-SQL-oder SQLCLR-Prozedur zu debuggen, und der Debugger keine Debugmeldungen vom SQL Server empfängt.

Dieses Problem kann aufgrund von Netzwerkproblemen oder Problemen bei der SQL Server auftreten, aber die wahrscheinlichste Ursache ist ein Berechtigungsproblem.

Zwei Konten sind beteiligt:

- Das Anwendungskonto ist das Benutzerkonto, unter dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird.

- Das Verbindungskonto ist die Identität, mit der die Verbindung zu SQL Server hergestellt wird. Dieses Konto ist nicht notwendigerweise identisch mit der Identität, die in Visual Studio ausgeführt wird, als ob die Verbindung die SQL-Authentifizierung verwendet.

  Beim SQL-Debugging muss das Anwendungs Konto dem Verbindungs Konto entsprechen oder ein sysadmin sein.

  Wenn Sie einen SQL-Kontonamen wie SA verwenden, muss das Anwendungs Konto auf dem SQL Server als sysadmin eingerichtet werden. Standardmäßig sind Administratoren auf dem Computer, auf dem SQL Server ausgeführt wird, SQL Server Sysadmins.

  So können Sie diesen Fehler korrigieren:

  - Überprüfen Sie die Berechtigungseinstellungen. Weitere Informationen finden Sie unter Gewusst [wie: Festlegen SQL Server Berechtigungen für das Debuggen](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Stellen Sie sicher, dass SQL-Debuggen ordnungsgemäß eingerichtet ist.

  - Weitere Informationen erhalten Sie vom Netzwerk- oder Datenbankadministrator.

## <a name="see-also"></a>Siehe auch

- [Einrichten des SQL-Debuggens](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Vorgehensweise: Festlegen von SQL Server Berechtigungen für das Debuggen](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)