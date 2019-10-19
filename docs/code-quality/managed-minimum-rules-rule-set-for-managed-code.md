---
title: Regelsatz für verwaltete Mindestregeln für verwalteten Code
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 10758bbabeb21f00ea10dd779bc6a44acdcc6bba
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535788"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Regelsatz für verwaltete Mindestregeln für verwalteten Code

Die verwalteten minimal Regeln konzentrieren sich auf die kritischsten Probleme in Ihrem Code, darunter potenzielle Sicherheitslücken, Anwendungs Abstürze und andere wichtige Logik-und Entwurfs Fehler. Fügen Sie diesen Regelsatz in einen benutzerdefinierten Regelsatz ein, den Sie für Ihre Projekte erstellen.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1821](../code-quality/ca1821.md)|Leere Finalizer entfernen.|
|[CA2213](../code-quality/ca2213.md)|Verwerfbare Felder verwerfen.|
|[CA2231](../code-quality/ca2231.md)|Gleichheits Operator beim Überschreiben von `ValueType.Equals`|
