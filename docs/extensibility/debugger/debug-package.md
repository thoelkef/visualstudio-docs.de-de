---
title: Debugpaket | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739022"
---
# <a name="debug-package"></a>Debug-Paket
Das Debugpaket wird in der Visual Studio-Shell ausgeführt und verarbeitet die gesamte Benutzeroberfläche. Es verwendet die Visual Studio-Debugschnittstellen und kommuniziert mit dem Sitzungsdebug-Manager (SDM).

 Durch den SDM-SDM gesendete Unterbrechungsereignisse wechseln Sie den Debugger vom Ausführungsmodus in den Unterbrechungsmodus und ändern Sie den Fokus auf das Programm, in dem die Unterbrechung aufgetreten ist. Das Debugpaket verfolgt den Stapelrahmen und den Thread anhand der Informationen, die von den Ereignissen an das Paket gesendet werden.

 Das Debugpaket hat keine Sprach- oder Laufzeitumgebungsabhängigkeiten. Es ist nicht erforderlich, das Debugpaket zu implementieren oder zu ändern.

 Das Debugpaket wird von *vsdebug.dll*implementiert.

## <a name="see-also"></a>Weitere Informationen
- [Sitzungsdebug-Manager](../../extensibility/debugger/session-debug-manager.md)
- [Stapelrahmen](../../extensibility/debugger/stack-frames.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
