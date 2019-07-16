---
title: 'CA2228: Nicht freigegebene Ressourcenformate nicht veröffentlichen.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f8a672056c8663c2e27ec730e542083aee9738f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714979"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nicht freigegebene Ressourcenformate nicht veröffentlichen.

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine Ressourcendatei erstellt wurde, mit einer Version von .NET, die derzeit nicht unterstützt wird.

## <a name="rule-description"></a>Regelbeschreibung

Ressourcendateien, die mithilfe von Vorabversionen von .NET erstellt wurden, möglicherweise nicht von den unterstützten Versionen von .NET verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, erstellen Sie die Ressource mit einer unterstützten Version von .NET.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.
