---
title: Die ausgewählte Verbindung nutzt einen nicht unterstützten Anbieter.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c59716342a26607842adca1e896177de2eb3facc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000184"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Die ausgewählte Verbindung nutzt einen nicht unterstützten Anbieter.

Diese Meldung wird angezeigt, wenn Sie Elemente ziehen, die nicht die .NET Framework-Datenanbieter für SQL Server verwenden **Server-Explorer** oder **Datenbank-Explorer** auf die [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

Die **O/R Designer** unterstützt nur datenverbindungen, die den .NET Framework-Datenanbieter für SQL Server verwenden. Nur Verbindungen zu Microsoft SQL Server oder zur Microsoft SQL Server-Datenbankdatei sind gültig.

Um diesen Fehler zu beheben, fügen Sie nur Elemente von datenverbindungen, die .NET Framework-Datenanbieter für SQL Server verwenden, die **O/R Designer**.

## <a name="see-also"></a>Siehe auch

- <xref:System.Data.SqlClient>
- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
