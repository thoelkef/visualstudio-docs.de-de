---
title: Grafik-Frame Überprüfung | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9732cd3f3440448e5096e71f838d8ebcf20fb13
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473958"
---
# <a name="graphics-frame-validation"></a>Grafik-Frame-Überprüfung
<!-- VERSIONLESS -->
Visual Studio-2017 und mehr Unterstützung der **Frame Überprüfung** Tool.  Die Frame-Validierung Fenster zeigt Fehler und Warnungen, die die Ereignisliste zugeordnet.  Um dieses Fenster anzuzeigen, wählen Sie die **Ansicht > Frame Überprüfung** Menü.

![Frame-Überprüfung](media/gfx_diag_frame_validation.png)

Klicken Sie auf die **Überprüfung ausführen** Schaltfläche in der oberen linken Ecke auf die Analyse zu initiieren.  Dauert möglicherweise mehrere Minuten je nach Komplexität des Frames.  Die Daten, die angezeigt wird, wird hier eine Kombination aus beiden Quellen: Nachrichten, D3D selbst ausgibt, wenn [SDK Ebenen](https://msdn.microsoft.com/library/windows/desktop/ff476881(v=vs.85).aspx) aktiviert ist, und die vom Nachverfolgen von internen Zustand des Tools gesammelten Daten. Sobald der Vorgang abgeschlossen ist, sehen Sie mehrere Spalten mit Daten:

**Spalte**|**Beschreibung**
---|---
Ereignis-ID | ID, die auf einen Eintrag im ordnet die [Ereignisliste](graphics-event-list.md) Fenster.
Schweregrad | Beschädigung, Fehler, Warnung, Information oder Nachricht.
Kategorie | Anwendung definiert ist, verschiedene, Initialisierung, Bereinigung, Kompilierung, State Erstellung, Status festlegen, Status abrufen, Ausführung, Ressource Manipulation, Shader, redundante und nicht verwendete.
Nachricht | Die Meldung, die dem Ereignis zugeordnet wird.
Ereignis | Das Ereignis, das den Fehler oder die Warnung zugeordnet.

## <a name="see-also"></a>Siehe auch  
[Grafikdiagnose (Debuggen DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->