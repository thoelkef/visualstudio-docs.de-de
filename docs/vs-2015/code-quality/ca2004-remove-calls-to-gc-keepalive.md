---
title: 'CA2004: Aufrufe von GC zu entfernen. KeepAlive | Microsoft-Dokumentation'
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
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e9d7e9a833c71145b97b4f9c0e979e6e415b6628
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182031"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Aufrufe an GC.KeepAlive entfernen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Klassen geben mit `SafeHandle` , aber dennoch enthält Aufrufe von `GC.KeepAlive`.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn Sie zum Konvertieren `SafeHandle` Nutzung, entfernen Sie alle Aufrufe `GC.KeepAlive` (Objekt). In diesem Fall Klassen dürfen keine aufzurufende `GC.KeepAlive`, vorausgesetzt, sie haben keinen Finalizer, sondern basieren auf `SafeHandle` das Betriebssystemhandle für diese durchführen.  Obwohl die Kosten für einen Aufruf von `GC.KeepAlive` möglicherweise unerheblich, wie die Wahrnehmung der Leistung gemessen, die einen Aufruf von `GC.KeepAlive` erforderlich oder ausreichend, um eine Lebensdauer zu lösen, Problem, das möglicherweise nicht mehr vorhanden. Dadurch wird der Code schwieriger zu, verwalten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie Aufrufe von `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können diese Warnung unterdrücken, nur dann, wenn er nicht technisch korrekt zu konvertieren ist `SafeHandle` Nutzung in Ihrer Klasse.



