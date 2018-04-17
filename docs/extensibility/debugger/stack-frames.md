---
title: Stapelrahmen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: feb2bc9d87486b6f83cf4b19ecec24c8c03edee5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="stack-frames"></a>Stapelrahmen
Im Hinblick auf die Architektur des Debuggers einen **Stapelrahmen**:  
  
-   Ist eine Abstraktion von einem Stapel, der den Ausführungskontext eines Threads bereitstellt. Ein Thread, die immer innerhalb einer Funktion ausgeführt wird. Stack-Frame enthält die lokalen Variablen der Funktion und die Argumente zu. Um mit Visual Studio zu debuggen, muss die Sprache oder die Umgebung, die zu debuggenden Stapelrahmen unterstützen.  
  
-   Kann sowohl zu identifizieren und selbst beschreiben und den zugeordneten Thread zurückgeben kann. Ein Stapelrahmen kann auch der Codekontext, der den aktuellen Anweisungszeiger sowie die zugehörige Dokumentation darstellt und Auswertung in Ausdruck zurückgeben.  
  
-   Verfügt über Eigenschaften, die den Namen, Typ und Wert der lokalen Variablen und Argumente beschreiben, und die in verschiedene IDE-Debug-Fenster angezeigt werden.  
  
-   Dargestellt durch eine [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) Schnittstelle, die in der Regel durch einen Debugging-Modul (DE) oder die virtuelle Maschine als Folge eines Threads erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Debuggen des Datenbankmoduls](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)