---
title: 'CA2228: Führen Sie nicht freigegebene Ressourcenformate'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e6f2216d26315491e7e187acdd31530c0bcf013
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829075"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Führen Sie nicht freigegebene Ressourcenformate

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Ressourcendatei erstellt wurde, mit einer Version von .NET Framework, die derzeit nicht unterstützt wird.

## <a name="rule-description"></a>Regelbeschreibung
 Ressourcendateien, die mithilfe von Vorabversionen von .NET Framework erstellt wurden, möglicherweise nicht von den unterstützten Versionen von .NET Framework verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, erstellen Sie die Ressource mit einer unterstützten Version von .NET Framework.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.
