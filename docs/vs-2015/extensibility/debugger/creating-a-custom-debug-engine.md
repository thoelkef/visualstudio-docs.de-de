---
title: Erstellen einer benutzerdefinierten Debug-Engine | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841243"
---
# <a name="creating-a-custom-debug-engine"></a>Erstellen einer benutzerdefinierten Debug-Engine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine Debug-Engine (de) ist eine Komponente, die das Debuggen bestimmter Lauf Zeit Architekturen ermöglicht. Es gibt in der Regel nur eine de-Implementierung pro Laufzeitumgebung.  
  
> [!NOTE]
> Obwohl es separate de-Implementierungen für Transact-SQL und JScript gibt, verwenden VBScript und JScript eine einzelne de.  
  
 Ein de funktioniert mit dem Interpreter oder dem Betriebssystem, um solche debuggingdienste als Ausführungs Steuerung, Breakpoints und Ausdrucks Auswertung bereitzustellen. Diese Dienste werden über die de-Schnittstellen implementiert und können dazu führen, dass der Debugger zwischen verschiedenen Betriebsmodi übergeht. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).  
  
 Das Erstellen eines de besteht aus den folgenden Schritten:  
  
1. Registrieren einer de mit Visual Studio  
  
2. Aktivieren eines deaktivierte Programms  
  
3. Ausführungs Steuerung und Zustands Auswertung  
  
4. Senden von Ereignissen  
  
5. Beendigung und trennen  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Registrieren einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Erläutert die erforderlichen Schritte zum Registrieren einer Debug-Engine in Visual Studio, damit Sie verwendet werden kann.  
  
 [Aktivieren eines Programms für das Debuggen](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Erläutert, dass Sie vor dem Debuggen eines Programms das Programm zuerst starten oder an ein vorhandenes Programm Anfügen müssen.  
  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Erläutert, warum beim Debuggen einer Anwendung Ausführungs Steuerungsfunktionen implementiert werden müssen.  
  
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)  
 Beschreibt die Kommunikation zwischen dem Debugger und der de als Ereignis Modell, das auf DCOM basiert.  
  
 [Beenden und Trennen](../../extensibility/debugger/termination-and-detaching.md)  
 Erläutert das Erreichen der normalen Beendigung, d. h., es gibt keine Haltepunkte, Ausnahmen, Laufzeitfehler oder unendliche Schleifen in der zu debuggenden Anwendung.  
  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumentiert die Aufruf Reihenfolge der Ereignisse, die in einer Debugsitzung auftreten.  
  
 [Gewusst wie: Debuggen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Erläutert, wie eine benutzerdefinierte de debuggt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
