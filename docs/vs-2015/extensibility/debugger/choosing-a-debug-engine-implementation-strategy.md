---
title: Auswählen einer Strategie für die Debug-Engine-Implementierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183469"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Auswählen einer Implementierungsstrategie für die Debug-Engine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie die Lauf Zeit Architektur, um die Implementierung der Debug-Engine (de) zu bestimmen. Die Debug-Engine wird möglicherweise Prozess Weise in das zu debuggende Programm, in Bearbeitung mit dem Visual Studio Session Debug Manager (SDM) oder außerhalb des Prozesses für beide Prozesse erstellt. Die folgenden Richtlinien sollten Ihnen helfen, zwischen diesen drei Strategien zu wählen.  
  
## <a name="guidelines"></a>Richtlinien  
 Obwohl es möglich ist, dass der Dienst außerhalb des Prozesses sowohl für das SDM als auch für das zu debuggende Programm verwendet wird, gibt es in der Regel keinen Grund dafür. Aufrufe über Prozess Grenzen hinweg sind relativ langsam.  
  
 Debug-engines werden bereits für die native Win32-Laufzeitumgebung und für die Common Language Runtime Umgebung bereitgestellt. Wenn Sie den de für eine dieser Umgebungen ersetzen müssen, müssen Sie den Prozess internen Prozess mit dem SDM erstellen.  
  
 Andernfalls können Sie auswählen, ob Sie den Prozess internen Prozess für die SDM-oder Prozess interne Erstellung des zu debuggenden Programms durchgeführt haben. Es ist wichtig zu berücksichtigen, ob die Ausdrucks Auswertung der de häufig auf den Programmsymbol Speicher zugreifen muss und ob der Symbol Speicher für den schnellen Zugriff in den Arbeitsspeicher geladen werden kann. Berücksichtigen Sie außerdem folgende Punkte:  
  
- Wenn es nicht viele Aufrufe zwischen der Ausdrucks Auswertung und dem Symbol Speicher gibt, oder wenn der Symbol Speicher in den SDM-Speicherbereich eingelesen werden kann, erstellen Sie den Prozess internen Prozess für die SDM. Sie müssen die CLSID der Debug-Engine an die SDM zurückgeben, wenn Sie an Ihr Programm angefügt wird. Der SDM verwendet diese CLSID, um eine Prozess interne Instanz von de zu erstellen.  
  
- Wenn das Programm das Programm aufrufen muss, um auf den Symbol Speicher zuzugreifen, erstellen Sie den Prozess internen Prozess mit dem Programm. In diesem Fall erstellt das Programm die Instanz von de.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
