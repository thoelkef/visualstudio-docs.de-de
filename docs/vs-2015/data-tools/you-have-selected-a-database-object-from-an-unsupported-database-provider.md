---
title: Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 05a4407eba52ec3940b70ffab220ef354af90e9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657792"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) Unterstützt nur die .NET Framework Datenanbieter für SQL Server ( <xref:System.Data.SqlClient> ). Obwohl Sie auf **OK** klicken und die Arbeit an Objekten von nicht unterstützten Datenbankanbietern fortsetzen können, kann zur Laufzeit unerwartetes Verhalten auftreten.

> [!NOTE]
> Es werden nur Datenverbindungen unterstützt, die den .NET Framework-Datenanbieter für SQL Server verwenden.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Klicken Sie auf **OK**, um mit dem Entwerfen der Entitätsklassen fortzufahren, die der Verbindung mit dem nicht unterstützten Datenbankanbieter zugeordnet sind. Es kann unerwartetes Verhalten auftreten, wenn nicht unterstützte Datenbankanbieter verwendet werden.

     - oder -

- Klicken Sie auf **Abbrechen**.

     Die Aktion wird beendet. Erstellen oder verwenden Sie eine Datenverbindung, die .NET Framework-Anbieter für SQL Server verwendet.

## <a name="see-also"></a>Weitere Informationen
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [.NET Framework-Datenanbietern](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)