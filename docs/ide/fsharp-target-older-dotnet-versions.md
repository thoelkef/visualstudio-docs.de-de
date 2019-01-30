---
title: Vorherige .NET Framework-Zielversionen für F#
description: Hier erhalten Sie Informationen zur älteren .NET Framework-Zielversion bei der Verwendung von F# in Visual Studio.
ms.date: 07/11/2018
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 88a689461fd5417800c6243950f296fde18fb3a1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970941"
---
# <a name="target-older-versions-of-net-f"></a>Ältere .NET-Zielversionen (F#)

Der folgende Fehler wird möglicherweise angezeigt, wenn Sie versuchen, .NET Framework 2.0, 3.0 oder 3.5 in einem F#-Projekt zur Zielversion zu machen, wenn Visual Studio unter Windows 8.1 installiert ist:

**Für dieses Projekt muss die Laufzeit 2.0 F# installiert sein, diese Laufzeit ist jedoch nicht installiert.**

Dieser Fehler tritt in der Regel unter folgenden Kombinationen von Bedingungen auf:

- Sie haben Visual Studio unter Windows 8.1 installiert.

- Vor der Installation von Visual Studio haben Sie .NET Framework 3.5 nicht aktiviert.

- Zielframework in Ihrem Projekt ist .NET Framework 2.0, 3.0 oder 3.5.

Bei der Installation von Visual Studio wird die installierte Version von .NET-Framework erkannt. Visual Studio installiert die Laufzeit F# 2.0 nur dann, wenn .NET Framework 3.5 installiert und aktiviert ist.

## <a name="resolve-the-error"></a>Beheben des Fehlers

So beheben Sie diesen Fehler:

- Richten Sie .NET Framework nach einer neueren Version aus.

- Aktivieren Sie .NET Framework 3.5 unter Windows 8.1, und installieren Sie anschließend die Laufzeit F# 2.0, indem Sie die Installation von Visual Studio reparieren. Führen Sie hierzu die folgenden Schritte aus.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>So aktivieren Sie .NET Framework 3.5 unter Windows 8.1

1. Geben Sie in der Anzeige **Start** **Systemsteuerung** ein.

   Während der Eingabe wird unter der Überschrift **Apps** das Symbol für **Systemsteuerung** angezeigt.

2. Wählen Sie das Symbol für **Systemsteuerung**, das Symbol für **Programme** und anschließend den Link **Windows-Funktionen ein- oder ausschalten** aus.

3. Stellen Sie sicher, dass das Kontrollkästchen **.NET Framework 3.5 (einschließlich .NET 2.0 und 3.0)** aktiviert ist, und klicken Sie anschließend auf die Schaltfläche **OK**. Bei untergeordneten Knoten für optionale Komponenten von .NET-Framework müssen die Kontrollkästchen nicht aktiviert werden.

   Sofern noch nicht geschehen, wird .NET Framework 3.5 aktiviert.

### <a name="to-install-the-f-20-runtime"></a>So installieren Sie die Laufzeit F# 2.0

Führen Sie die [Schritte zum Reparieren von Visual Studio 2017](../install/repair-visual-studio.md) aus.

## <a name="see-also"></a>Siehe auch

- [Leitfaden für F# (.NET Framework)](/dotnet/fsharp/)
- [F# in Visual Studio](fsharp-visual-studio.md)