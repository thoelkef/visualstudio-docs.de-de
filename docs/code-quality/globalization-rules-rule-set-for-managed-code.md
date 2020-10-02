---
title: Regelsatz für Globalisierungsregeln für verwalteten Code
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0c3b899ec8e19160d9ee4a307a86c576d217004c
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658541"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Regelsatz für Globalisierungsregeln für verwalteten Code

Verwenden Sie den Regelsatz Microsoft-Globalisierungsregeln, um sich auf Probleme zu konzentrieren, die möglicherweise verhindern, dass Daten in Ihrer Anwendung in verschiedenen Sprachen, Gebiets Schemata und Kulturen ordnungsgemäß angezeigt werden. Sie sollten diesen Regelsatz einschließen, wenn Ihre Anwendung lokalisiert, globalisiert oder beides ist.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Literale nicht als lokalisierte Parameter übergeben.|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|CultureInfo angeben.|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|IFormatProvider angeben.|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|StringComparison zur Übersichtlichkeit angeben|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Zeichenfolgen in Großbuchstaben normalisieren.|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Ordinal-StringComparison verwenden.|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|StringComparison für Richtigkeit angeben|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.|
