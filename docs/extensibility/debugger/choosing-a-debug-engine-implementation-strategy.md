---
title: Auswählen einer Debug-Engine-Implementierungsstrategie | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739130"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Auswählen einer Debug-Engine-Implementierungsstrategie
Verwenden Sie die Laufzeitarchitektur, um die Implementierungsstrategie des Debugmoduls (DE) zu bestimmen. Sie können das Debugmodul in dem Programm erstellen, das Sie debuggen. Erstellen Sie das Debugmodul im Prozess für den Visual Studio-Sitzungsdebug-Manager (SDM). Oder erstellen Sie das Debugmodul out-of-Process für beide. Die folgenden Richtlinien sollten Ihnen bei der Auswahl dieser drei Strategien helfen.

## <a name="guidelines"></a>Richtlinien
 Während es möglich ist, dass die DE sowohl für das SDM als auch für das Programm, das Sie debuggen, a-process ist, gibt es in der Regel keinen Grund, dies zu tun. Aufrufe über Prozessgrenzen hinweg sind relativ langsam.

 Debugmodule werden bereits für die native Win32-Laufzeitumgebung und für die Common Language-Laufzeitumgebung bereitgestellt. Wenn Sie die DE für eine der beiden Umgebungen ersetzen müssen, sollten Sie die DE-in-Process mit dem SDM erstellen.

 Andernfalls erstellen Sie entweder die DE-in-Process-Datei für das SDM oder die In-Process-Datei für das Programm, das Sie debuggen. Sie müssen überlegen, ob der Ausdrucksauswertungswert des DE häufigen Zugriff auf den Programmsymbolspeicher erfordert. Oder, wenn der Symbolspeicher für den schnellen Zugriff in den Speicher geladen werden kann. Berücksichtigen Sie auch die folgenden Ansätze:

- Wenn zwischen dem Ausdrucksauswertungswert und dem Symbolspeicher nicht viele Aufrufe vorhanden sind oder der Symbolspeicher in den SDM-Speichereinlesebereich eingelesen werden kann, erstellen Sie die DE-In-Process-Datei für das SDM. Sie müssen die CLSID des Debugmoduls an das SDM zurückgeben, wenn es an Ihr Programm angefügt wird. Das SDM verwendet diese CLSID, um eine Prozessinstanz der DE zu erstellen.

- Wenn die DE das Programm aufrufen muss, um auf den Symbolspeicher zuzugreifen, erstellen Sie die DE-in-Process mit dem Programm. In diesem Fall erstellt das Programm die Instanz der DE.

## <a name="see-also"></a>Weitere Informationen
- [Erweiterbarkeit des Visual Studio-Debuggers](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
