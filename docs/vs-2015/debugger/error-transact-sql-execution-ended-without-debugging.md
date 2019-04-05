---
title: 'Fehler: Ausführen von Transact-SQL wurde ohne Debuggen beendet. | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 910b84e7a024547208ea2e7ae1d6a6897cf60893
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "58962258"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Fehler: Das Ausführen von Transact-SQL wurde ohne Debuggen beendet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieser Fehler tritt auf, wenn Sie versuchen, eine Transact-SQL- oder SQL/CLR-Prozedur zu debuggen und der Debugger keine Debugmeldungen vom SQL-Server erhält.  
  
 Dies kann durch Netzwerkprobleme oder Probleme auf dem SQL-Server verursacht worden sein, aber die wahrscheinlichste Ursache ist ein Berechtigungsproblem.  
  
 Zwei Konten sind beteiligt:  
  
- Das Anwendungskonto ist das Benutzerkonto, unter dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausgeführt wird.  
  
- Das Verbindungskonto ist die Identität, mit der die Verbindung zu SQL Server hergestellt wird. Dies ist nicht notwendigerweise die gleiche Identität, unter der Visual Studio ausgeführt wird, wenn die Verbindung SQL-Authentifizierung verwendet.  
  
  SQL-Debuggen erfordert, dass das Anwendungskonto mit dem Verbindungskonto übereinstimmen muss oder Systemadministratorrechte hat.  
  
  Wenn Sie einen SQL-Benutzernamen wie sa verwenden, muss das Anwendungskonto auf dem SQL-Server als Systemadministrator eingerichtet sein. Standardmäßig sind Administratoren auf dem Computer, auf dem SQL Server ausgeführt wird, SQL Server-Systemadministratoren.  
  
  So können Sie diesen Fehler korrigieren:  
  
- Überprüfen Sie die Berechtigungseinstellungen. Weitere Informationen finden Sie unter [Vorgehensweise: Legen Sie die SQL Server-Berechtigungen für das Debuggen](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
- Stellen Sie sicher, dass SQL-Debuggen ordnungsgemäß eingerichtet ist.  
  
- Weitere Informationen erhalten Sie vom Netzwerk- oder Datenbankadministrator.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten von SQL-Debugging](http://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Vorgehensweise: Legen Sie die SQL Server-Berechtigungen für das Debuggen](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
