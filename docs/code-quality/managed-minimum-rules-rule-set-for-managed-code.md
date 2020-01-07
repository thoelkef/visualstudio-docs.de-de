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
ms.openlocfilehash: 95264aafd2467065ee2bc36d463369f19714dd68
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587354"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Regelsatz für verwaltete Mindestregeln für verwalteten Code

Die verwalteten minimal Regeln konzentrieren sich auf die kritischsten Probleme in Ihrem Code, darunter potenzielle Sicherheitslücken, Anwendungs Abstürze und andere wichtige Logik-und Entwurfs Fehler. Fügen Sie diesen Regelsatz in einen benutzerdefinierten Regelsatz ein, den Sie für Ihre Projekte erstellen.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1821](../code-quality/ca1821.md)|Leere Finalizer entfernen.|
|[CA2213](../code-quality/ca2213.md)|Verwerfbare Felder verwerfen.|
|[CA2231](../code-quality/ca2231.md)|Gleichheits Operator beim Überschreiben von `ValueType.Equals`|
