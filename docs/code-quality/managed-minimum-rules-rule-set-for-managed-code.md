---
title: Regelsatz für verwaltete Mindestregeln für verwalteten Code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c929abe75a22e705cc86f256dbbf7942280149d0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013287"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Regelsatz für verwaltete Mindestregeln für verwalteten Code

Die verwaltete Mindestregeln konzentrieren sich auf die kritischsten Probleme in Ihrem Code, einschließlich potenzieller Sicherheitslücken, Anwendungsabstürze und anderen wichtigen Logik- und Designfehlern. Enthalten Sie in allen benutzerdefinierten Regelsätzen, dass Sie für Ihre Projekte erstellen.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Leere Finalizer entfernen.|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Verwerfbare Felder verwerfen.|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|
