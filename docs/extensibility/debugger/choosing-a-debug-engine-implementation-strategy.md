---
title: Auswählen einer Strategie für die Debug-Engine-Implementierung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739130"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Auswählen einer Strategie für die Debug-Engine-Implementierung
Verwenden Sie die Lauf Zeit Architektur, um die Implementierung der Debug-Engine (de) zu bestimmen. Sie können die Debug-Engine in-Process mit dem Programm erstellen, das Sie Debuggen. Erstellen Sie die Debug-Engine in-Process mit dem Visual Studio Session Debug Manager (SDM). Oder erstellen Sie die Debug-Engine außerhalb des Prozesses für beide. Die folgenden Richtlinien sollten Ihnen bei der Auswahl dieser drei Strategien helfen.

## <a name="guidelines"></a>Richtlinien
 Obwohl es möglich ist, dass der Dienst außerhalb des Prozesses sowohl für das SDM als auch für das Programm, das Sie Debuggen, verwendet werden kann, gibt es in der Regel keinen Grund dafür. Aufrufe über Prozess Grenzen hinweg sind relativ langsam.

 Debug-engines werden bereits für die native Win32-Laufzeitumgebung und für die Common Language Run-Time-Umgebung bereitgestellt. Wenn Sie die de für eine der beiden Umgebungen ersetzen müssen, sollten Sie den Prozess internen Prozess mit dem SDM erstellen.

 Andernfalls erstellen Sie entweder den Prozess "de in-Process" für die SDM oder in-Process mit dem Programm, das Sie Debuggen. Sie müssen bedenken, ob die Ausdrucks Auswertung der de häufig auf den Programmsymbol Speicher zugreifen muss. Oder, wenn der Symbol Speicher für den schnellen Zugriff in den Arbeitsspeicher geladen werden kann. Beachten Sie auch die folgenden Ansätze:

- Wenn es nicht viele Aufrufe zwischen der Ausdrucks Auswertung und dem Symbol Speicher gibt, oder wenn der Symbol Speicher in den SDM-Speicherbereich eingelesen werden kann, erstellen Sie den Prozess internen Prozess für die SDM. Sie müssen die CLSID der Debug-Engine an die SDM zurückgeben, wenn Sie an Ihr Programm angefügt wird. Der SDM verwendet diese CLSID, um eine Prozess interne Instanz von de zu erstellen.

- Wenn das Programm das Programm aufrufen muss, um auf den Symbol Speicher zuzugreifen, erstellen Sie den Prozess internen Prozess mit dem Programm. In diesem Fall erstellt das Programm die Instanz von de.

## <a name="see-also"></a>Weitere Informationen
- [Erweiterbarkeit von Visual Studio-Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
