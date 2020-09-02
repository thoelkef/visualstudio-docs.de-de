---
title: Stapel Rahmen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3050e89db2f5cbb138f3d358b10c7cd936c560e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423386"
---
# <a name="stack-frames"></a>Stapelrahmen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur ein **Stapel Rahmen**:  
  
- Eine Abstraktion eines Stapels, der den Ausführungs Kontext eines Threads bereitstellt. Ein Thread wird immer innerhalb einer Funktion ausgeführt. Ein Stapel Rahmen enthält die lokalen Variablen der Funktion und die Argumente für Sie. Zum Debuggen mit Visual Studio muss die zu debuggende Sprache oder Umgebung Stapel Rahmen unterstützen.  
  
- Kann identifizieren und beschreiben und den zugeordneten Thread zurückgeben. Ein Stapel Rahmen kann auch den Code Kontext zurückgeben, der den aktuellen Anweisungs Zeiger darstellt, sowie die zugeordneten Kontexte der Dokumentation und Ausdrucks Auswertung.  
  
- Verfügt über Eigenschaften, die den Namen, den Typ und den Wert lokaler Variablen und Argumente beschreiben und in verschiedenen IDE-Debugfenstern angezeigt werden.  
  
- Wird durch eine [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle dargestellt, die in der Regel durch eine Debug-Engine (de) oder eine virtuelle Maschine erstellt wird, wenn ein Thread ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
