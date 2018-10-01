---
title: 'Fehler: Ein Transact-SQL-Ausführung wurde ohne Debuggen beendet. | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7de8aaba3abf4ef7c767ed549b5454b1599e808d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523666"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Fehler: Das Ausführen von Transact-SQL wurde ohne Debuggen beendet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Fehler: Ausführen von Transact-SQL wurde ohne Debuggen beendet](https://docs.microsoft.com/visualstudio/debugger/error-transact-sql-execution-ended-without-debugging).  
  
Dieser Fehler tritt auf, wenn Sie versuchen, eine Transact-SQL- oder SQL/CLR-Prozedur zu debuggen und der Debugger keine Debugmeldungen vom SQL-Server erhält.  
  
 Dies kann durch Netzwerkprobleme oder Probleme auf dem SQL-Server verursacht worden sein, aber die wahrscheinlichste Ursache ist ein Berechtigungsproblem.  
  
 Zwei Konten sind beteiligt:  
  
-   Das Anwendungskonto ist das Benutzerkonto, unter dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausgeführt wird.  
  
-   Das Verbindungskonto ist die Identität, mit der die Verbindung zu SQL Server hergestellt wird. Dies ist nicht notwendigerweise die gleiche Identität, unter der Visual Studio ausgeführt wird, wenn die Verbindung SQL-Authentifizierung verwendet.  
  
 SQL-Debuggen erfordert, dass das Anwendungskonto mit dem Verbindungskonto übereinstimmen muss oder Systemadministratorrechte hat.  
  
 Wenn Sie einen SQL-Benutzernamen wie sa verwenden, muss das Anwendungskonto auf dem SQL-Server als Systemadministrator eingerichtet sein. Standardmäßig sind Administratoren auf dem Computer, auf dem SQL Server ausgeführt wird, SQL Server-Systemadministratoren.  
  
 So können Sie diesen Fehler korrigieren:  
  
-   Überprüfen Sie die Berechtigungseinstellungen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von SQL Server-Berechtigungen zum Debugging](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Stellen Sie sicher, dass SQL-Debuggen ordnungsgemäß eingerichtet ist.  
  
-   Weitere Informationen erhalten Sie vom Netzwerk- oder Datenbankadministrator.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten von SQL-Debugging](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Vorgehensweise: Festlegen von SQL Server-Berechtigungen für das Debuggen](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)



