---
title: Nicht unterstützter Datenbankanbieter
description: Die ausgewählte Verbindung nutzt einen nicht unterstützten Anbieter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c8fa073b47927f673914156c586bf27a121e53ea
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037568"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Die ausgewählte Verbindung nutzt einen nicht unterstützten Anbieter.

Diese Meldung wird angezeigt, wenn Sie Elemente ziehen, die nicht den .NET Framework Datenanbieter für SQL Server von **Server-Explorer** oder **Datenbank-Explorer** auf die [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)verwenden.

Der **O/R-Designer** unterstützt nur Datenverbindungen, bei denen der .NET Framework Anbieter für SQL Server verwendet wird. Nur Verbindungen zu Microsoft SQL Server oder zur Microsoft SQL Server-Datenbankdatei sind gültig.

Um diesen Fehler zu beheben, fügen Sie nur Elemente aus Datenverbindungen hinzu, die die .NET Framework Datenanbieter für die SQL Server zum **O/R-Designer**verwenden.

## <a name="see-also"></a>Weitere Informationen

- <xref:System.Data.SqlClient>
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
