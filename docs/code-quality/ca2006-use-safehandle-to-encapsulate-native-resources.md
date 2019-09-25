---
title: 'CA2006: SafeHandle verwenden, um native Ressourcen zu kapseln.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0e671deab060346bb998932495e5590f19945eaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233101"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: SafeHandle verwenden, um native Ressourcen zu kapseln.

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Verwalteter Code <xref:System.IntPtr> verwendet für den Zugriff auf native Ressourcen.

## <a name="rule-description"></a>Regelbeschreibung

Die Verwendung `IntPtr` von in verwaltetem Code kann auf ein potenzielles Sicherheits-und Zuverlässigkeits Problem hindeuten. Alle Verwendungsmöglichkeiten `IntPtr` von müssen überprüft werden, um zu bestimmen, ob <xref:System.Runtime.InteropServices.SafeHandle> die Verwendung von oder einer ähnlichen Technologie notwendig ist. Es treten Probleme auf, `IntPtr` wenn die eine systemeigene Ressource (z. b. Arbeitsspeicher, ein Datei Handle oder einen Socket) darstellt, die der verwaltete Code als Besitzer hat. Wenn der verwaltete Code die Ressource besitzt, muss er auch die ihm zugeordneten systemeigenen Ressourcen freigeben, da ein Ausfall nicht zu einer Ressourcen Lecks führen würde.

In solchen Szenarien bestehen auch Sicherheits-oder Zuverlässigkeitsprobleme, wenn der `IntPtr` Multithread-Zugriff auf zulässig ist und eine Möglichkeit besteht, die durch die `IntPtr` dargestellte Ressource freizugeben. Diese Probleme umfassen die `IntPtr` Wiederverwendung des Werts in der Ressourcen Freigabe, während die gleichzeitige Verwendung der Ressource auf einem anderen Thread erfolgt. Dies kann Racebedingungen verursachen, bei denen ein Thread Daten lesen oder schreiben kann, die mit der falschen Ressource verknüpft sind. Wenn Ihr Typ z. b. ein Betriebssystem Handle als `IntPtr` speichert und es Benutzern ermöglicht, sowohl **Close** als auch eine beliebige andere Methode aufzurufen, die dieses Handle gleichzeitig und ohne Synchronisierung verwendet, hat der Code ein Problem beim wieder verwenden.

Diese Problembehandlung kann zu Daten Beschädigungen und häufig zu einem Sicherheitsrisiko führen. `SafeHandle`und die gleich geordnete Klasse <xref:System.Runtime.InteropServices.CriticalHandle> bieten einen Mechanismus zum Kapseln eines nativen Handles für eine Ressource, damit solche Threading Probleme vermieden werden können. Darüber hinaus können Sie und `SafeHandle` seine gleich geordnete Klasse `CriticalHandle` für andere Threading Probleme verwenden, um z. b. die Lebensdauer von verwalteten Objekten sorgfältig zu steuern, die eine Kopie des nativen Handles über Aufrufe von systemeigenen Methoden enthalten. In dieser Situation können Sie häufig Aufrufe von `GC.KeepAlive`entfernen. Der Leistungs Aufwand, den Sie bei der Verwendung `SafeHandle` von und in geringerem `CriticalHandle`Maße verursachen, kann häufig durch einen sorgfältigen Entwurf reduziert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Konvertieren `IntPtr` Sie die `SafeHandle` Verwendung in, um den Zugriff auf native Ressourcen sicher zu verwalten. Beispiele finden <xref:System.Runtime.InteropServices.SafeHandle> Sie im Referenz Artikel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Diese Warnung nicht unterdrücken.

## <a name="see-also"></a>Siehe auch

- <xref:System.IDisposable>