---
title: Aktivieren ein Programm, das gedebuggt werden | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a581c5a9ae56f52727c011db1de2ad35a5ba3592
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-a-program-to-be-debugged"></a>Aktivieren ein Programm, das gedebuggt werden
Bevor Ihre Debugging-Modul (DE) ein Programm debuggen kann, müssen Sie zuerst starten die DE oder fügen Sie es an ein vorhandenes Programm handelt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Abrufen eines Ports](../../extensibility/debugger/getting-a-port.md)  
 Erläutert, wie Sie einen Port nicht als der erste Schritt zur Aktivierung eines Programms, das gedebuggt werden abgerufen.  
  
 [Registrieren des Programms](../../extensibility/debugger/registering-the-program.md)  
 Der nächste Schritt bei der Aktivierung der ein Programm, das gedebuggt werden erläutert: Registrieren es mit dem Port. Nach der Registrierung kann die Anwendung gedebuggt werden entweder durch Anfügen oder das Just-in-Time (JIT) Debuggen.  
  
 [Anfügen an das Programm](../../extensibility/debugger/attaching-to-the-program.md)  
 Den nächsten Schritt erläutert: Anfügen des Debuggers an die Anwendung.  
  
 [Start-basierte Anfügen](../../extensibility/debugger/launch-based-attachment.md)  
 Beschreibt, Start-basierte Anlage an ein Programm, die beim Start durch die SDM automatisch ausgeführt wird.  
  
 [Senden der erforderlichen Ereignisse](../../extensibility/debugger/sending-the-required-events.md)  
 Führt Sie schrittweise durch die erforderlichen Ereignisse für die Erstellung einer Debugging-Modul (DE), und es an ein Programm anfügen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definiert einen Debugging-Modul (DE), und beschreibt Dienste implementiert, über die DE-Schnittstellen und wie sie den Debugger für den Übergang zwischen den verschiedenen Betriebsmodi verursachen können.