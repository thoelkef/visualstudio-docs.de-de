---
title: Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 13e6dd42ed372fb28d850a566ea1900447ad220c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909511"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.

Die **O/R Designer** unterstützt nur die .NET Framework-Datenanbieter für SQL Server (<xref:System.Data.SqlClient>). Obwohl Sie auf **OK** klicken und die Arbeit an Objekten von nicht unterstützten Datenbankanbietern fortsetzen können, kann zur Laufzeit unerwartetes Verhalten auftreten.

> [!NOTE]
> Es werden nur Datenverbindungen unterstützt, die den .NET Framework-Datenanbieter für SQL Server verwenden.

## <a name="options"></a>Optionen

- Klicken Sie auf **OK**, um mit dem Entwerfen der Entitätsklassen fortzufahren, die der Verbindung mit dem nicht unterstützten Datenbankanbieter zugeordnet sind. Es kann unerwartetes Verhalten auftreten, wenn nicht unterstützte Datenbankanbieter verwendet werden.

- Klicken Sie auf **Abbrechen** zum Beenden des. Erstellen Sie oder verwenden Sie eine andere Datenverbindung, die den .NET Framework-Datenanbieter für SQL Server verwendet.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)