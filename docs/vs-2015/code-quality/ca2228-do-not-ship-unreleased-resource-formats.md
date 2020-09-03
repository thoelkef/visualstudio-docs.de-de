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
ms.openlocfilehash: 4adcae1c1cc616cdbcf5a7aa15342d221c2f4300
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540581"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nicht freigegebene Ressourcenformate nicht veröffentlichen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Ressourcen Datei wurde mit einer Version von erstellt [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , die derzeit nicht unterstützt wird.

## <a name="rule-description"></a>Beschreibung der Regel
 Ressourcen Dateien, die mithilfe von vorab Versionen von erstellt wurden, können [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] möglicherweise nicht von unterstützten Versionen der .NET Framework verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, erstellen Sie die Ressource mit einer unterstützten Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] k.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.
