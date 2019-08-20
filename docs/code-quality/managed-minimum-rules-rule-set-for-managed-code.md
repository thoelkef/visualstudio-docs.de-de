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
ms.openlocfilehash: 183923a764cc3462e799c8f67677aa564c5fe59d
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585130"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Regelsatz für verwaltete Mindestregeln für verwalteten Code

Die verwalteten minimal Regeln konzentrieren sich auf die kritischsten Probleme in Ihrem Code, darunter potenzielle Sicherheitslücken, Anwendungs Abstürze und andere wichtige Logik-und Entwurfs Fehler. Fügen Sie diesen Regelsatz in einen benutzerdefinierten Regelsatz ein, den Sie für Ihre Projekte erstellen.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Leere Finalizer entfernen.|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Verwerfbare Felder verwerfen.|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Gleichheits Operator beim Überschreiben`ValueType.Equals`|
