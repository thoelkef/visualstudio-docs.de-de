---
title: Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b1dd14c428b90b87e665aa41681b5a9e68eb00e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648018"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.

Der **O/R-Designer** unterstützt nur die .NET Framework Datenanbieter für SQL Server (<xref:System.Data.SqlClient>). Obwohl Sie auf **OK** klicken und die Arbeit an Objekten von nicht unterstützten Datenbankanbietern fortsetzen können, kann zur Laufzeit unerwartetes Verhalten auftreten.

> [!NOTE]
> Es werden nur Datenverbindungen unterstützt, die den .NET Framework-Datenanbieter für SQL Server verwenden.

## <a name="options"></a>Optionen

- Klicken Sie auf **OK**, um mit dem Entwerfen der Entitätsklassen fortzufahren, die der Verbindung mit dem nicht unterstützten Datenbankanbieter zugeordnet sind. Es kann unerwartetes Verhalten auftreten, wenn nicht unterstützte Datenbankanbieter verwendet werden.

- Klicken Sie auf **Abbrechen** , um die Aktion zu beenden. Erstellen oder verwenden Sie eine andere Datenverbindung, die den .NET Framework Anbieter für SQL Server verwendet.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)