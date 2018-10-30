---
title: 'Fehler: Benutzer konnte nicht führen Sie die gespeicherte Prozedur "sp_enable_sql_debug" | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 561bc9b96ff12309ae9bc9ba7ea58cef16074361
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922236"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Fehler: Der Benutzer konnte die gespeicherte Prozedur "sp_enable_sql_debug" nicht ausführen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die gespeicherte Prozedur "sp_enable_sql_debug" konnte auf dem Server nicht ausgeführt werden. Mögliche Ursachen:  
  
- Ein Verbindungsproblem. Es muss eine stabile Verbindung mit dem Server bestehen.  
  
- Fehlende erforderliche Berechtigungen für den Server. Zum Debuggen auf SQL Server 2005 müssen sowohl das Konto, unter dem Visual Studio ausgeführt wird, als auch das Konto, unter dem die Verbindung mit SQL Server hergestellt wird, Mitglieder der Systemadministratoren-Rolle sein. Das Konto, mit dem die Verbindung mit SQL Server hergestellt wird, ist entweder das Windows-Benutzerkonto (bei Windows-Authentifizierung) oder ein Konto mit Benutzer-ID und Kennwort (bei SQL-Authentifizierung).  
  
  Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von SQL Server-Berechtigungen zum Debugging](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Festlegen von SQL Server-Berechtigungen für das Debuggen](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Einrichten von SQL-Debugging](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)



