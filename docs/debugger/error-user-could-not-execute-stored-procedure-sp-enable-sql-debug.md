---
title: 'Fehler: Benutzer konnte nicht führen Sie die gespeicherte Prozedur "sp_enable_sql_debug" | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b121b863237a3b12b5131be348581ea3fd043d2
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348567"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Fehler: Der Benutzer konnte die gespeicherte Prozedur „sp_enable_sql_debug“ nicht ausführen

Die gespeicherte Prozedur "sp_enable_sql_debug" konnte auf dem Server nicht ausgeführt werden. Mögliche Ursachen:

- Ein Verbindungsproblem. Es muss eine stabile Verbindung mit dem Server bestehen.

- Fehlende erforderliche Berechtigungen für den Server. Zum Debuggen auf SQL Server 2005 müssen sowohl das Konto, unter dem Visual Studio ausgeführt wird, als auch das Konto, unter dem die Verbindung mit SQL Server hergestellt wird, Mitglieder der Systemadministratoren-Rolle sein. Das Konto, mit dem die Verbindung mit SQL Server hergestellt wird, ist entweder das Windows-Benutzerkonto (bei Windows-Authentifizierung) oder ein Konto mit Benutzer-ID und Kennwort (bei SQL-Authentifizierung).

Weitere Informationen finden Sie unter [Vorgehensweise: Legen Sie die SQL Server-Berechtigungen für das Debuggen](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Legen Sie die SQL Server-Berechtigungen für das Debuggen](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Einrichten von SQL-Debugging](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))