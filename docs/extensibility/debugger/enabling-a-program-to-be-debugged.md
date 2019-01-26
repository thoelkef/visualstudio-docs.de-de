---
title: Aktivieren eines Programms zu debuggende | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8faa677e5893c0737bcd89db5567ef7459f6d07
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953225"
---
# <a name="enable-a-program-to-be-debugged"></a>Aktivieren Sie zu debuggenden Programm
Bevor der Debug-Engine (DE) ein Programm debuggen kann, müssen Sie die DE starten oder fügen Sie ihn an ein vorhandenes Programm.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Abrufen eines Ports](../../extensibility/debugger/getting-a-port.md)  
 Erläutert, wie Sie einen Port als der erste Schritt zum Aktivieren eines Programms, die debuggt werden abgerufen.  
  
 [Registrieren Sie das Programm](../../extensibility/debugger/registering-the-program.md)  
 Der nächste Schritt bei der Aktivierung der zu debuggenden Programm erläutert: Registrieren sie mit dem Port. Nach der Registrierung kann die Anwendung debuggt werden entweder durch den Prozess anfügen oder das Debuggen von just-in-Time (JIT).  
  
 [Fügen an die Anwendung an](../../extensibility/debugger/attaching-to-the-program.md)  
 Im nächsten Schritt erläutert: Anfügen des Debuggers an die Anwendung.  
  
 [Start-basierte Anfügen](../../extensibility/debugger/launch-based-attachment.md)  
 Beschreibt die startbasiertes um ein Programm, das automatisch beim Start durch die SDM ist.  
  
 [Senden Sie die erforderlichen Ereignisse](../../extensibility/debugger/sending-the-required-events.md)  
 Führt Sie schrittweise durch die erforderlichen Ereignisse, die beim Erstellen einer Debug-Engine (DE), und es an ein Programm angefügt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen einer benutzerdefinierten Debug-engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definiert eine Debug-Engine (DE) und beschreibt die Dienste, die über die DE-Schnittstellen und wie sie den Debugger für den Übergang zwischen verschiedenen Betriebsmodi verursachen können.