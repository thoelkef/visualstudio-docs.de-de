---
title: Threads | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 028ad25495ba01d9763c8bec3bbb9c4480d72ff8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185360"
---
# <a name="threads"></a>Threads
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur ist ein **Thread**:  
  
- Ist die grundlegende Einheit der Berechnung. Ein Thread führt seine Anweisungen sequenziell innerhalb des Kontexts einer einzelnen Rückruf Stapel aus und wechselt von einem Code Kontext zum nächsten.  
  
- Kann sich selbst und das Programm identifizieren, in dem es ausgeführt wird, und kann benannt, angehalten und fortgesetzt werden. Ein Thread kann auch seine zugeordneten Stapel Rahmen auflisten und unter bestimmten Bedingungen in einen anderen Stapel Rahmen verschieben. Bei einem Kontext eines Stapel Rahmens kann ein Thread ggf. den zugeordneten logischen Thread zurückgeben. Ein Thread verfügt über Eigenschaften, z. b. eine Unterbrechungs Anzahl, die im Thread Fenster der IDE angezeigt werden kann.  
  
- Wird durch eine [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) -Schnittstelle dargestellt, die in der Regel durch eine Debug-Engine (de) oder eine virtuelle Maschine erstellt wird, wenn ein Programm ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programme](../../extensibility/debugger/programs.md)   
 [Stapel Rahmen](../../extensibility/debugger/stack-frames.md)   
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Sitzungsbasierter Debug-Manager](../../extensibility/debugger/session-debug-manager.md)
