---
title: Regelsatz für verwaltete Mindestregeln für verwalteten Code
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 903b464172d541277de5fbac6d8ab035578b6154
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658502"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Regelsatz für verwaltete Mindestregeln für verwalteten Code

Die verwalteten minimal Regeln konzentrieren sich auf die kritischsten Probleme in Ihrem Code, darunter potenzielle Sicherheitslücken, Anwendungs Abstürze und andere wichtige Logik-und Entwurfs Fehler. Fügen Sie diesen Regelsatz in einen benutzerdefinierten Regelsatz ein, den Sie für Ihre Projekte erstellen.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Leere Finalizer entfernen.|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Verwerfbare Felder verwerfen.|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Gleichheits Operator beim Überschreiben `ValueType.Equals`|
