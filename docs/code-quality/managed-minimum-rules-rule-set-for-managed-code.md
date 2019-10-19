---
title: Regelsatz für verwaltete Mindestregeln für verwalteten Code
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: efb282d8876d48d4f8e7eb81963719e2d14e5900
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649254"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Regelsatz für verwaltete Mindestregeln für verwalteten Code

Die verwalteten minimal Regeln konzentrieren sich auf die kritischsten Probleme in Ihrem Code, darunter potenzielle Sicherheitslücken, Anwendungs Abstürze und andere wichtige Logik-und Entwurfs Fehler. Fügen Sie diesen Regelsatz in einen benutzerdefinierten Regelsatz ein, den Sie für Ihre Projekte erstellen.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1821](../code-quality/ca1821.md)|Leere Finalizer entfernen.|
|[CA2213](../code-quality/ca2213.md)|Verwerfbare Felder verwerfen.|
|[CA2231](../code-quality/ca2231.md)|Gleichheits Operator beim Überschreiben von `ValueType.Equals`|
