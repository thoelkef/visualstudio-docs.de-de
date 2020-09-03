---
title: 'CA2004: Entfernen Sie die Aufrufe von GC. KeepAlive | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53fa5f61cb7c503502956831452bc3eca1a9fece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521198"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Aufrufe an GC.KeepAlive entfernen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Category|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Klassen verwenden `SafeHandle` , aber enthalten weiterhin Aufrufe von `GC.KeepAlive` .

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn Sie in die Verwendung von umrechnen `SafeHandle` , entfernen Sie alle Aufrufe von `GC.KeepAlive` (-Objekt). In diesem Fall dürfen Klassen nicht aufzurufen `GC.KeepAlive` , wenn Sie keinen Finalizer haben, sondern sich darauf verlassen, `SafeHandle` das Betriebssystem Handle für Sie abzuschließen.  Obwohl die Kosten für die `GC.KeepAlive` Beibehaltung eines Aufrufes durch die Leistung vernachlässigbar sein können, ist der Eindruck, dass ein aufrufender `GC.KeepAlive` entweder notwendig oder ausreichend ist, um ein Lebensdauer Problem zu lösen, das möglicherweise nicht mehr vorhanden ist, die Verwaltung des Codes erschwert.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie Aufrufe von `GC.KeepAlive` .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können diese Warnung nur unterdrücken, wenn die Konvertierung in `SafeHandle` die Verwendung in ihrer Klasse nicht technisch korrekt ist.
