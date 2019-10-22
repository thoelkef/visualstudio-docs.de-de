---
title: 'CA2228: nicht freigegebene Ressourcen Formate nicht versenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9297ea0bb24eed54d0134a5f3c0fce87e6757adb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662885"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nicht freigegebene Ressourcenformate nicht veröffentlichen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Ressourcen Datei wurde mit einer Version der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] erstellt, die derzeit nicht unterstützt wird.

## <a name="rule-description"></a>Regelbeschreibung
 Ressourcen Dateien, die mithilfe von vorab Versionen der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] erstellt wurden, können möglicherweise nicht von unterstützten Versionen der .NET Framework verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, erstellen Sie die Ressource mit einer unterstützten Version der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.
