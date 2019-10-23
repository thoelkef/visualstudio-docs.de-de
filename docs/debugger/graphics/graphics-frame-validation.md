---
title: Grafik Frame-Validierung | Microsoft-Dokumentation
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49248c6209f9e56e51551f6cd3d4af66ecac8b56
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735502"
---
# <a name="graphics-frame-validation"></a>Grafik Frame Validierung
<!-- VERSIONLESS -->
Visual Studio 2017 und höher unterstützen das **Frame Validierungs** Tool.  Im Fensterrahmen Validierung werden Fehler und Warnungen angezeigt, die der Ereignisliste zugeordnet sind.  Um dieses Fenster anzuzeigen, wählen Sie das Menü **> Frame-Überprüfung anzeigen** aus.

![Frame-Überprüfung](media/gfx_diag_frame_validation.png)

Klicken Sie in der oberen linken Ecke auf die Schaltfläche **Validierung ausführen** , um die Analyse zu initiieren.  Je nach Komplexität des Frames kann es mehrere Minuten dauern, bis der Vorgang abgeschlossen ist.  Bei den hier angezeigten Daten handelt es sich um eine Kombination aus zwei Quellen: die Nachrichten, die von D3D selbst ausgegeben werden, wenn die [SDK-Ebenen](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) aktiviert sind, und die Daten, die von der eigenen internen Zustandsüberwachung des Tools gesammelt werden Nach Abschluss des Vorgangs werden mehrere Datenspalten angezeigt:

| **Spalte** | **Beschreibung** |
|------------| - |
| Ereignis-ID | ID, die einem Eintrag im Fenster [Ereignisliste](graphics-event-list.md) zugeordnet ist. |
| Schweregrad | Beschädigung, Fehler, Warnung, Info oder Meldung. |
| Kategorie | Anwendung definiert, Sonstiges, Initialisierung, Bereinigung, Kompilierung, Zustands Erstellung, Zustands Einstellung, Status Erstellung, Ausführung, Ressourcen Bearbeitung, Shader, redundant und nicht verwendet. |
| Nachricht | Die Meldung, die dem Ereignis zugeordnet ist. |
| event | Das Ereignis, das dem Fehler oder der Warnung zugeordnet ist. |

## <a name="see-also"></a>Siehe auch
[Grafikdiagnose (Debuggen von DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->