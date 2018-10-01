---
title: Betriebsmodi | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b23ba695b02a0332ad40a2c51047336903255a13
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522799"
---
# <a name="operational-modes"></a>Betriebsmodi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Betriebsmodi](https://docs.microsoft.com/visualstudio/extensibility/debugger/operational-modes).  
  
Es gibt drei Modi, die in denen IDE, wie folgt verwendet werden kann:  
  
-   [Entwurfsmodus](#vsconoperationalmodesanchor1)  
  
-   [Ausführungsmodus](#vsconoperationalmodesanchor2)  
  
-   [Unterbrechungsmodus](#vsconoperationalmodesanchor3)  
  
 Wie Ihre benutzerdefinierten Debug-Engine (DE) zwischen diesen Modus wechselt, ist eine implementierungsentscheidung, die Sie mit der übergangsmechanismen vertraut sein muss. Die DE kann oder dieser Modi kann nicht direkt implementieren. Diese Modi sind tatsächlich Debug Paket Modi, die Schalter basierend auf der Benutzeraktion oder Ereignisse aus dem DE. Der Übergang vom ausführungs-in den Unterbrechungsmodus ist z. B. durch eine Beenden-Ereignis aus dem DE ausgelöst hat. Der Übergang von Unterbrechung entweder oder Schritt Modus ausgeführt wird durch den Benutzer, die Vorgänge wie z. B. Schritt oder Execute ausgelöst hat. Weitere Informationen zu DE Übergänge, finden Sie unter [Steuern der Ausführung von](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Entwurfsmodus  
 Im Entwurfsmodus ist der nonrunning Zustand Visual Studio zu debuggen, während dieses, den Zeitraums Debugfunktionen in Ihrer Anwendung festlegen können.  
  
 Nur ein paar Debuggen während der Entwurfsmodus Features verwendet werden. Entwickler kann auch Haltepunkte festzulegen, oder sehen Sie sich Ausdrücke erstellen. Die DE wird nie geladen oder aufgerufen, während die IDE im Entwurfsmodus befindet. Interaktion mit der er findet statt, während der Ausführung und Break-Modi.  
  
##  <a name="vsconoperationalmodesanchor2"></a> Ausführungsmodus  
 Ausführungsmodus tritt auf, wenn ein Programm in einer Debugsitzung in der IDE ausgeführt wird. Die Anwendung führt bis zum Beenden, bis ein Haltepunkt erreicht wird, oder eine Ausnahme ausgelöst wird. Wenn die Anwendung zu beenden, die DE-Übergänge im Entwurfsmodus ausgeführt wird. Wenn ein Haltepunkt erreicht wird, oder eine Ausnahme ausgelöst wird, geht die DE, um in den Unterbrechungsmodus.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Unterbrechungsmodus  
 Im Unterbrechungsmodus tritt auf, wenn die Ausführung des Programms Debuggen angehalten wird. Im Unterbrechungsmodus bietet dem Entwickler einen Überblick über die Anwendung zum Zeitpunkt der Unterbrechung und ermöglicht dem Entwickler, die den Status der Anwendung analysieren und zu ändern, wie die Anwendung ausgeführt wird. Der Entwickler kann anzeigen und Bearbeiten von Code, zu überprüfen oder Ändern von Daten, die Anwendung neu starten, Ausführung beenden oder Fortsetzen der Ausführung an der Stelle.  
  
 Im Unterbrechungsmodus eingegeben wird, wenn die DE eine synchrone Stopping-Ereignis sendet. Synchrone beenden-Ereignissen, die Ereignisse zu beenden, so genannte benachrichtigen der sitzungsbasierter Debug-Manager (SDM) und die IDE, die die Anwendung im Debugmodus befindlichen Ausführen von Code beendet wurde. Die [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) und [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) Schnittstellen sind Beispiele für die beenden-Ereignissen.  
  
 Beenden Ereignisse werden durch einen Aufruf einer der folgenden Methoden, fortgesetzt, die den Debugger im Unterbrechungsmodus auszuführen oder Schritt Modus wechseln:  
  
-   [Execute](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Schritt-Modus  
 Schritt-Modus tritt auf, wenn das Programm die nächste Zeile von Code oder in, überspringen oder aus einer Funktion der Schritte. Ein Schritt wird ausgeführt, durch Aufrufen der Methode [Schritt](../../extensibility/debugger/reference/idebugprocess3-step.md). Diese Methode erfordert `DWORD`s, die angeben, die [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) und [STEPKIND](../../extensibility/debugger/reference/stepkind.md) Enumerationen als Eingabeparameter.  
  
 Wenn das Programm erfolgreich Schritte aus, um die nächste Zeile des Codes oder in einer Funktion oder erfolgt die Ausführung bis zum Cursor oder um einen Haltepunkt festlegen, die DE erfolgt automatisch ein Übergang zurück, um den Unterbrechungsmodus.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuern der Ausführung](../../extensibility/debugger/control-of-execution.md)

