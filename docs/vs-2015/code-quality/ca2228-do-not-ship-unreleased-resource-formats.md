---
title: 'CA2228: Führen Sie nicht freigegebene Ressourcenformate | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eb5e595062ca39ba644499012981c78d7a986ced
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917527"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nicht freigegebene Ressourcenformate nicht veröffentlichen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Ressourcendatei erstellt wurde, mit einer Version von der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , wird derzeit nicht unterstützt.

## <a name="rule-description"></a>Regelbeschreibung
 Ressourcendateien, die erstellt wurden, mithilfe von Vorabversionen von der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] kann nicht von den unterstützten Versionen von .NET Framework verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, erstellen Sie die Ressource, die mit einer unterstützten Version von der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.



