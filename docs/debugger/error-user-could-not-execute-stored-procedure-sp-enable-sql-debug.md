---
title: "Fehler: Benutzer können keine gespeicherte Prozedur ausführen \"sp_enable_sql_debug\" | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5da5a9aa6bc5f2bda382b69223b2b758f576ac29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Fehler: Der Benutzer konnte die gespeicherte Prozedur "sp_enable_sql_debug" nicht ausführen
Die gespeicherte Prozedur "sp_enable_sql_debug" konnte auf dem Server nicht ausgeführt werden. Mögliche Ursachen:  
  
-   Ein Verbindungsproblem. Es muss eine stabile Verbindung mit dem Server bestehen.  
  
-   Fehlende erforderliche Berechtigungen für den Server. Zum Debuggen auf SQL Server 2005 müssen sowohl das Konto, unter dem Visual Studio ausgeführt wird, als auch das Konto, unter dem die Verbindung mit SQL Server hergestellt wird, Mitglieder der Systemadministratoren-Rolle sein. Das Konto, mit dem die Verbindung mit SQL Server hergestellt wird, ist entweder das Windows-Benutzerkonto (bei Windows-Authentifizierung) oder ein Konto mit Benutzer-ID und Kennwort (bei SQL-Authentifizierung).  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von SQL Server-Berechtigungen zum Debugging](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Festlegen von SQL Server-Berechtigungen für das Debuggen](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Einrichten von SQL-Debuggen](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)