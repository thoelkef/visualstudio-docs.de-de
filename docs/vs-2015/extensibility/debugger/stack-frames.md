---
title: Stapelrahmen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 301a782ebf0eda9b1e97c9f0f09c10a0985de4c2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271595"
---
# <a name="stack-frames"></a>Stapelrahmen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur eine **Stapelrahmen**:  
  
-   Ist eine Abstraktion eines Stapels, der den Ausführungskontext eines Threads bereitstellt. Ein Thread wird immer innerhalb einer Funktion ausgeführt. Ein Stapelrahmen werden die lokalen Variablen der Funktion und die Argumente, enthält. Um mit Visual Studio zu debuggen, muss die Sprache oder Umgebung, die im Debugmodus befindlichen Stapelrahmen unterstützen.  
  
-   Kann sowohl zu identifizieren und selbst beschreiben und können den zugeordneten Thread zurück. Ein Stapelrahmen kann der Codekontext, der den aktuellen Anweisungszeiger, sowie die zugehörige Dokumentation darstellt und ausdruckskontexten-Auswertung zurückgegeben werden.  
  
-   Verfügt über Eigenschaften, die den Namen, Typ und Wert der lokalen Variablen und Argumente, die beschreiben, und die in verschiedene IDE-Debug-Fenster angezeigt werden.  
  
-   Wird durch dargestellt eine [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) Schnittstelle, die in der Regel von einem Debug-Engine (DE) oder den virtuellen Computer als Folge eines Threads erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)

