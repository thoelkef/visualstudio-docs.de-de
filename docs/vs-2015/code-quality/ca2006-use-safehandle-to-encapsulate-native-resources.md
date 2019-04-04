---
title: 'CA2006: SafeHandle verwenden, um systemeigene Ressourcen zu kapseln | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dcf385263eba5a6012097f43b49e7a75166bad42
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958710"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: SafeHandle verwenden, um native Ressourcen zu kapseln.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 In verwaltetem Code wird verwendet <xref:System.IntPtr> Zugriff auf systemeigene Ressourcen.

## <a name="rule-description"></a>Regelbeschreibung
 Verwenden von `IntPtr` in verwaltetem Code möglicherweise ein potenzielles Problem für Sicherheit und Zuverlässigkeit. Alle Verwendungen des `IntPtr` muss überprüft werden, um zu bestimmen, ob die Verwendung von einer <xref:System.Runtime.InteropServices.SafeHandle> , oder eine ähnliche Technologie an seiner Stelle erforderlich ist. Probleme tritt auf, wenn die `IntPtr` stellt eine systemeigene Ressource, z. B. Arbeitsspeicher, ein Dateihandle oder einen Socket, dass der verwaltete Code als Besitzer betrachtet wird. Wenn der verwaltete Code die Ressource besitzt, müssen sie außerdem die systemeigenen Ressourcen zugeordnet, freigeben, da ein Fehler dazu Ressource Datenlecks verursachen würde.

 In solchen Szenarien Sicherheit oder Zuverlässigkeit Probleme ist ebenfalls vorhanden, wenn Speicherzugriffs in Multithreadanwendungen darf die `IntPtr` zum Freigeben der Ressource, die durch dargestellt wird, und die `IntPtr` wird bereitgestellt. Diese Probleme beinhalten die Wiederverwendung von der `IntPtr` Wert auf einer Ressourcenfreigabe, während gleichzeitige Verwendung der Ressource in einem anderen Thread erfolgt. Dies kann zu Racebedingungen führen, in denen ein Thread Lese- oder Schreibzugriff auf Daten, die falsche Ressource zugeordnet ist. Wenn Ihr Typ ein Betriebssystemhandle als speichert z. B. eine `IntPtr` und ermöglicht Benutzern, die beide rufen **schließen** und jede andere Methode, die dieses Handle gleichzeitig und ohne eine Art der Synchronisierung verwendet werden, Ihren Code verfügt über ein Handle wiederverwenden Problem.

 Dieses Handle, das Problem beim Recyceln kann es sich um beschädigte Daten und in vielen Fällen ein Sicherheitsrisiko führen. `SafeHandle` und seine nebengeordnete Klasse <xref:System.Runtime.InteropServices.CriticalHandle> bieten einen Mechanismus, um ein systemeigenes Handle auf eine Ressource zu kapseln, damit solche Threadingprobleme vermieden werden können. Darüber hinaus können Sie `SafeHandle` und seine nebengeordnete Klasse `CriticalHandle` für andere Threadingprobleme, z. B. um die Lebensdauer von verwalteten Objekten sorgfältig zu steuern, die eine Kopie der das systemeigene Handle über Aufrufe an systemeigene Methoden enthalten. In diesem Fall kann häufig beseitigt werden Aufrufe von `GC.KeepAlive`. Die Leistung Mehraufwand alle fallen bei Verwendung von `SafeHandle` und in geringerem Maße `CriticalHandle`, häufig durch einen sorgfältigen Entwurf reduziert werden können.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Konvertieren von `IntPtr` Nutzung `SafeHandle` um den Zugriff auf systemeigene Ressourcen sicher zu verwalten. Finden Sie unter den <xref:System.Runtime.InteropServices.SafeHandle> Referenzthema für Beispiele.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie sollten nicht auf diese Warnung unterdrücken.

## <a name="see-also"></a>Siehe auch
 <xref:System.IDisposable>
