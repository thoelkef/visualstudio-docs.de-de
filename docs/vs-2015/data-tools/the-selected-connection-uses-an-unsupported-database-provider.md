---
title: Die ausgewählte Verbindung verwendet einen nicht unterstützten Datenbankanbieter. Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e79d8408fba54cf192d51f9d2ead8c0ffafe1f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667193"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Die ausgewählte Verbindung nutzt einen nicht unterstützten Anbieter.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Meldung wird angezeigt, wenn Sie Elemente, die nicht die .NET Framework Datenanbieter für SQL Server verwenden, aus **Server-Explorer** / **Datenbank-Explorer** auf die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)ziehen.

 Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] unterstützt nur Datenverbindungen, die den .NET Framework-Anbieter für SQL Server verwenden. Nur Verbindungen zu Microsoft SQL Server oder zur Microsoft SQL Server-Datenbankdatei sind gültig.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Fügen Sie nur Elemente von Datenverbindungen hinzu, die den .NET Framework-Datenanbieter für SQL Server zu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] verwenden.

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Data.SqlClient>[.NET Framework Datenanbieter](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen (O-R-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)